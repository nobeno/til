## 永続アトリビュート実装(DynamoDBとPython)

### 参考
- https://developer.amazon.com/ja-JP/docs/alexa/hosted-skills/alexa-hosted-skills-session-persistence.html
- https://alexa-skills-kit-python-sdk.readthedocs.io/ja/latest/ATTRIBUTES.html

</br>

### 1.`requirements.txt`に依存関係記述
```
boto3==1.9.216
ask-sdk-core==1.11.0
ask-sdk-dynamodb-persistence-adapter==1.15.0
```

</br>

### 2.`lambda_function.py`ファイルにコードを追加
#### ①インポート
```python
import os
import boto3

from ask_sdk_core.skill_builder import CustomSkillBuilder
from ask_sdk_dynamodb.adapter import DynamoDbAdapter
```

</br>

#### ②DynamoDBの情報
```python
ddb_region = os.environ.get('DYNAMODB_PERSISTENCE_REGION')
ddb_table_name = os.environ.get('DYNAMODB_PERSISTENCE_TABLE_NAME')

ddb_resource = boto3.resource('dynamodb', region_name=ddb_region)
dynamodb_adapter = DynamoDbAdapter(table_name=ddb_table_name, create_table=False, dynamodb_resource=ddb_resource)
```

</br>

#### ③リクエストハンドラーを追加
```python
sb = CustomSkillBuilder(persistence_adapter = dynamodb_adapter)

sb.add_request_handler(LaunchRequestHandler())
sb.add_request_handler(CancelOrStopIntentHandler())
sb.add_request_handler(SessionEndedRequestHandler())
#
#その他のリクエストハンドラー
#
sb.add_exception_handler(CatchAllExceptionHandler())

lambda_handler = sb.lambda_handler()
```

</br>

#### ④アトリビュート保存
```python
def handle(self, handler_input):
    # type: (HandlerInput) -> Response
    attr = handler_input.attributes_manager.persistent_attributes
    if not attr:
        attr['counter'] = 0
        attr['state'] = 'ENDED'

    handler_input.attributes_manager.session_attributes = attr

    handler_input.attributes_manager.save_persistent_attributes()
    speak_output = ("おかえりなさい。保存されたカウンタは{}です.こんにちは、またはヘルプと言ってください".format(attr["counter"]))
    reprompt = “こんにちは、またはヘルプと言ってください。”
    return (
        handler_input.response_builder
            .speak(speak_output)
            .ask(reprompt)
            .response
    )
```

</br>

#### ⑤アトリビュートを取得
```python
def handle(self, handler_input):
    # type: (HandlerInput) -> Response
    session_attr = handler_input.attributes_manager.session_attributes
    session_attr['state'] = "STARTED"
    session_attr["counter"] += 1
    handler_input.attributes_manager.persistent_attributes = session_attr
    handler_input.attributes_manager.save_persistent_attributes()

    speak_output = ("ハローワールド！ 保存されたカウンタは{}です。".format(session_attr["counter"]))
    return (
        handler_input.response_builder
            .speak(speak_output)
            # .ask('ユーザーが応答できるようセッションを開いたままにする場合は再プロンプトを追加してください')
            .response
    )
```

</br>

#### ⑥アトリビュート削除
```python
def handle(self, handler_input):
    # type: (HandlerInput) -> Response
    session_attr = handler_input.attributes_manager.session_attributes
    session_attr['state'] = "ENDED"

    speak_output = ("さようなら。カウンタは{}です".format(session_attr[“counter”]))

    handler_input.attributes_manager.delete_persistent_attributes()
    return (
        handler_input.response_builder
            .speak(speak_output)
            .response
    )
 ```
