# AWS Bedrockの設定とモデルのデプロイ

個人アカウントでAWS Bedrockを設定し、ClaudeおよびLlama2 70BをDeployしてみました。  
ネットから拾ってきた情報を参考にしたら、比較的簡単に設定できました。

**参考資料**: [Amazon Bedrock使ってみた](https://www.insurtechlab.net/use_amazon_bedrock/)

## モデルのテストとリージョン

- **リージョン**: 
  - 東京リージョンでClaude
  - バージニア北部リージョンでClaude2とLlama2を試してみました。

- **プロンプト**: 
  - DataNormのGitHubにあった[プロンプト](https://github.com/dx-junkyard/OpenData-Bridge-DataNorm#chatgpt%E7%94%A8%E3%83%97%E3%83%AD%E3%83%B3%E3%83%97%E3%83%88%E3%83%86%E3%83%B3%E3%83%97%E3%83%AC%E3%83%BC%E3%83%88)を使用してみました。
```
異なる複数のフォーマットからなるcsvファイルを一つのフォーマットに統合したい。複数ファイルのうち、一つをmaster.csvとして、残りをslave[n].csvとする。このとき[n]は1以上の数字を想定する。
入力[input]としてmaster.csvとslave[n].csvを与えるので[rule]以下のルールに基づき、mapping_rules.jsonを作成してほしい。

[input]
master.csv
---
"施設種別","地区","保育園名","所在地","緯度","経度","種別","電話番号","入園可能月齢","保育年齢別定員　0歳","保育年齢別定員　1歳","保育年齢別定員　2歳","保育年齢別定員　3歳","保育年齢別定員　4歳","保育年齢別定員　5歳","保育年齢別定員　合計","短時間保育開始時間","短時間保育終了時間","標準時間開始時間","標準時間終了時間","延長保育対象月齢","延長保育","休園日","運営事業者(指定管理者)","保育園ホームページ"
"認可保育園","芝","48保育園","東京都港区芝五丁目n番","35.8484","139.747716","区立","03-0000-0000","3か月","18","26","30","30","30","30","164","9:00","17:00","7:15","18:15","1歳の誕生日","22:00まで","日・祝・年末年始",,"https://www.xxxx.jp/index.html"
---

slave1.csv
---
名称,郵便番号,住所,電話番号,関連ホームページ,緯度,経度
児童館,1740051,板橋区小豆沢,03-0000-0000,http://www.xxxx.jp/index.html,35.58055254,139.6960174
---

slave2.csv
---
名称,所在地,URL,電話番号,FAX,緯度,経度
家庭支援センター,江戸川区船堀n丁目,http://www.xxxx.jp/index.html,03-0000-0000,03-0000-0000,35.685187,139.8653337
---

slave3.csv
---
施設名,カテゴリ,所在地,方書,郵便番号,電話番号,開所時刻,閉所時刻,備考,緯度（施設出入口）,経度（施設出入口）,緯度（施設中心）,経度（施設中心）
市立第６保育園,子育て,稲城市坂浜,,2060822,042-000-000,7:00,19:00,,35.422436,139.484959,34.622479,139.485152
---


[rule]
1) 以下[input ex]のようにmaster.csvとslave[n].csvが与えられた場合、[output ex]のようなmapping_rules.jsonを出力する。
ここで注意してほしいのはそのような変換プログラムの作成ではなく、jsonファイル作成の依頼であるということ。
2) csvの項目名とデータの内容から、masterとslaveの項目の対応関係を推測し、同じと思われるmasterの項目１つと配列で与えられるslave[n]の項目の対応関係をjsonファイルにする。
3) masterの項目は必ず対応関係の配列の1番目に追加しておく。
4) 対応関係の配列に重複する項目は必要ない。
5) slaveに存在し、masterには存在しない項目は捨てて良い。
6) masterには存在し、slaveには存在しない項目は対応関係の配列に記載しなくてよい。
7) master.csvに存在する項目が、対応関係の配列で2番目以降に出現する場合、その項目は対応関係の配列から除外する。
8) 以下に示すのは１例であって、必要なのはrule 1〜7で示されたルールを厳守し、[input]の方で提示しているmasterの各項目へのslave[n]の対応関係を漏らさずmapping_rules.jsonとして出力することである。

[input ex]
master.csv
---
"施設種別","保育園名","所在地"
"認可保育園","shiba保育園","東京都港区芝五丁目"
---

slave1.csv
---
名称,住所,
さわ児童館,板橋区小豆沢
---

slave2.csv
---
施設名称,所在地,
家庭支援センター,江戸川区船堀4丁目2番
---

[output ex]
mapping_rules.json
---
{
    "保育園名":[
        "保育園名",
        "施設名",
        "施設名称"
    ],
    "所在地":[
        "所在地",
        "住所",
    ]
}
---
```

- **使用可能なモデル**:
  - 東京リージョンでは3モデル
    ![東京リージョンのモデル](screenshots/Model_access_region_Tokyo.png)
  - バージニア北部では19モデル
    ![バージニア北部のモデル](screenshots/Model_access_region_N%20California.png)
    

- **Claude2について**:
  - 東京リージョンではClaude2が使用できません。

- **その他**:
  - サンプル数と試したモデルの種類が少ないですが、Claude2が一番出力精度が良いと思いました。
  - ChatGPTのようなUI（会話履歴が残るタイプ）が簡単に作成できました。![実行イメージ](screenshots/chat_image.png)
    **参考資料1**: [Amazon Bedrock を利用して生成 AI でなにができるのか？を体験できる AWS のワークショップをやってみた](https://dev.classmethod.jp/articles/experiencing-generative-ai-with-amazon-bedrock-workshop/)  
    **参考資料2**: [生成系 AI 体験ワークショップ](https://catalog.workshops.aws/generative-ai-use-cases-jp/ja-JP)

## 設定と出力結果

以下は、各モデルの設定とパラメータです：

| 設定 | Claude v1.2 | Claude2 v1.2 | Llama 2 Chat 70B |
|------|-------------|--------------|------------------|
| DC Region | 東京 | バージニア北部 | バージニア北部 |
| Temperature | 1.0 | 1.0 | 0.5 |
| Top P | 0.999 | 0.999 | 0.9 |
| TopK | 250 | 250 |  |
| Maximum length | 1000 | 1000 |  |
| Response length |  |  | 1000 |
| Output | [Claude v1.2](output/Claude%20v1.2.txt) | [Claude2 v1.2](output/Claude2%20v1.2.txt) | [Llama 2 Chat 70B](output/Llama%202%20Chat%2070B.txt) |

**注釈**:[プロンプト](https://github.com/dx-junkyard/OpenData-Bridge-DataNorm#chatgpt%E7%94%A8%E3%83%97%E3%83%AD%E3%83%B3%E3%83%97%E3%83%88%E3%83%86%E3%83%B3%E3%83%97%E3%83%AC%E3%83%BC%E3%83%88)は全モデル共通です。
