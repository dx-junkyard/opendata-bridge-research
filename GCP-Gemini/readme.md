# Gemini Pro の設定とデプロイ

Gemini Proの推論をGoogle Colab及びGoogle AI Studioで実行しました。以下情報を参考に簡単に設定できました。  
個人的な所感かつかなりおおざっぱですが、GPT-3.5と同様の能力かと思われます。

### Google Colab
1. [Google Colab で Gemini Pro をもっと試す](https://note.com/npaka/n/n1c368639cada)  
   ⇒ これを参考に[notebook](notebook/Gemini%20Pro.ipynb)を作成。1分/60回まではAPIは無料のようです。
2. [Python Quickstart](https://colab.research.google.com/github/google/generative-ai-docs/blob/main/site/en/tutorials/python_quickstart.ipynb#scrollTo=lEXQ3OwKIa-O)

3. **PDFを読み込みCSVへ変換するコード。作成途中。**
   ```python
   import PyPDF2
   import pdfplumber  # PDFPlumberをインポート
   import pandas as pd
   import requests   # HTTPリクエスト用
   import json       # JSON操作用

   # PDFファイルを開いてテキストを抽出
   text = ""
   with pdfplumber.open('example.pdf') as pdf:
       for page in pdf.pages:
           text += page.extract_text()

   # ChatGPT APIを使用してテキストを解析する関数
   def analyze_text_with_chatgpt(text):
       # ChatGPT APIへのリクエストを作成（URLは架空）
       url = "https://api.openai.com/v1/chatgpt/analyze"
       headers = {
           "Authorization": "Bearer YOUR_API_KEY",  # 適切なAPIキーを設定
           "Content-Type": "application/json"
       }
       prompt = ("""異なるフォーマットからなるcsvファイルを一つのフォーマットに統合したい... [長いプロンプトはここで省略]""")
       payload = {
           "text": text,
           "instruction": prompt
       }
       response = requests.post(url, headers=headers, data=json.dumps(payload))

       if response.status_code == 200:
           return response.json()  # JSONレスポンスを返す
       else:
           raise Exception(f"ChatGPT API Error: {response.status_code}")

   # ChatGPT APIを使用してテキストを解析
   structured_data = analyze_text_with_chatgpt(text)

   # 解析されたデータをDataFrameに変換
   # 注: この部分は返されたデータに依存するため、適宜調整が必要
   df = pd.DataFrame(structured_data)

   # DataFrameをCSVファイルとして保存
   df.to_csv('output.csv', index=False)

### Google AI Studio(Gemini Pro)
以下が実行イメージ。Google AI Studioは、環境構築に手間がかからないイメージです。
画面右側にTemperatureなど設定項目があります。  

   ![Google AI Studio 実行イメージ](https://github.com/dx-junkyard/opendata-bridge-research/assets/115245862/55ce7c23-d020-47a1-9c03-c0fe5a482c9a)

### Google AI Studio(Gemini Pro Vision)
Google AI Studioでのファイル読み込みの方法がわからなかったため、試しにGemini Pro VisionでAED一覧のPDFの画像データを読み込ませてみた。
ところどころ間違えがある。

　　![image](https://github.com/dx-junkyard/opendata-bridge-research/assets/115245862/266e9af9-bf2d-47f6-9a38-fc263737b950)
  　![image](https://github.com/dx-junkyard/opendata-bridge-research/assets/115245862/659f77bf-523f-4506-9812-a75a59d2a34a)

