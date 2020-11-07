### beautifulsoup入門

- インストール  
  ```pip install beautifulsoup4```
  
  
- インポート  
  ```
  from bs4 import BeautifulSoup
  import urllib.request as req　 # urlを使用するためのライブラリ
  ```
  
  
- 使用例
  ```
  url = "https://weathernews.jp/s/solive24/timetable.html"  # 対象のurl
  response = req.urlopen(url)   # 指定したurlのHTMLを取得

  parse_html = BeautifulSoup(response,'html.parser')    # HTMLを解析

  print(parse_html.prettify())    # prettify：HTMLソースを整形して表示
  ```
  
  
- 参考： [Pythonで面倒な「ブラウザ操作」や「データ収集」の作業を自動化しよう｜Webスクレイピングのやり方をわかりやすく解説](https://www.youtube.com/watch?v=LgZ8Li97yoM&t=1693s&ab_channel=%E3%82%AD%E3%83%8E%E3%82%B3%E3%83%BC%E3%83%89%2F%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%9F%E3%83%B3%E3%82%B0%E5%AD%A6%E7%BF%92%E5%8B%95%E7%94%BB%E3%81%AEYouTuber)
