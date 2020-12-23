## DynamoDBを使う

### ドキュメント
https://boto3.amazonaws.com/v1/documentation/api/latest/guide/dynamccodb.html

### 準備
```python
import boto3
import json
from boto3.dynamodb.conditions import Key, Attr


dynamodb = boto3.resource('dynamodb')
table    = dynamodb.Table('MY_TABLE_NAME')
```

### query
```python
res = table.query(
        IndexName='MY_INDEX_NAME',
        KeyConditionExpression=Key('MY_INDEX_NAME').eq(MY_INDEX_VALUE)
    )
for row in res['Items']:
    print(row)

```

### put_item
```python
table.put_item(
    Item={
        "key1": value1,
        "key2": value2
   }
)
```

### get_item
```python
items = table.get_item(
            Key={
                 "key1": key1
            }
        )

```
