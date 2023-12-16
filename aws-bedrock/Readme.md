個人アカウントでAWS Bedrockを設定してClaude,Llama2 70BをDeployしてみました。
ネットから拾ってきた情報を参考にしたら比較的簡単にできました。

・東京リージョンでClaude、バージニア北部リージョンでClaude2,Llama2を試してみました。
・プロンプトとしてどのようなCSVを入力したらよいのかわからなかったので、OpenData-Bridge-
DataNormのGithubにあったプロンプトをとりあえず入力してみました
・東京リージョンは3モデル、バージニア北部は19モデル使用可能です
・東京リージョンではClaude2が使用できない
・サンプル数と試したモデルの種類が少なすぎますが、Claude2が一番出力精度が良いかと思いました
・ChatGPTのようなUI(会話した履歴が残る)が簡単にできたのでそれの実行イメージなどの情報共有します。

| 設定 | Claude v1.2 | Claude2 v1.2 | Llama 2 Chat 70B |
|------|-------------|--------------|------------------|
| [Amazon Bedrock使ってみた](https://www.insurtechlab.net/use_amazon_bedrock/) |  |  |  |
| DC Region | 東京 | バージニア北部 | バージニア北部 |
| Temperature | 1.0 | 1.0 | 0.5 |
| Top P | 0.999 | 0.999 | 0.9 |
| TopK | 250.0 | 250.0 |  |
| Maximum length | 1000.0 | 1000.0 |  |
| Response length |  |  | 1000.0 |
