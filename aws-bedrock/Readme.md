# AWS Bedrockの設定とモデルのデプロイ

個人アカウントでAWS Bedrockを設定し、ClaudeおよびLlama2 70BをDeployしてみました。ネットから拾ってきた情報を参考にしたら、比較的簡単に設定できました。

**参考資料**: [Amazon Bedrock使ってみた](https://www.insurtechlab.net/use_amazon_bedrock/)

## モデルのテストとリージョン

- **リージョン**: 
  - 東京リージョンでClaude
  - バージニア北部リージョンでClaude2とLlama2を試してみました。

- **プロンプト**: 
  - DataNormのGitHubにあった[プロンプト](https://github.com/dx-junkyard/OpenData-Bridge-DataNorm#chatgpt%E7%94%A8%E3%83%97%E3%83%AD%E3%83%B3%E3%83%97%E3%83%88%E3%83%86%E3%83%B3%E3%83%97%E3%83%AC%E3%83%BC%E3%83%88)を使用してみました。

- **使用可能なモデル**:
  - [東京リージョンでは3モデル](aws-bedrock/screenshots/Model_access_region_Tokyo.png)、[バージニア北部では19モデル](aws-bedrock/screenshots/Model_access_region_N%20California.png)が使用可能です。

- **Claude2について**:
  - 東京リージョンではClaude2が使用できません。

- **その他**:
  - サンプル数と試したモデルの種類が少ないですが、Claude2が一番出力精度が良いと思いました。
  - ChatGPTのようなUI（会話履歴が残るタイプ）が簡単に作成できました。実行イメージや関連情報を共有します。

## 設定とパラメータ

以下は、各モデルの設定とパラメータです：

| 設定 | Claude v1.2 | Claude2 v1.2 | Llama 2 Chat 70B |
|------|-------------|--------------|------------------|
| DC Region | 東京 | バージニア北部 | バージニア北部 |
| Temperature | 1.0 | 1.0 | 0.5 |
| Top P | 0.999 | 0.999 | 0.9 |
| TopK | 250 | 250 |  |
| Maximum length | 1000 | 1000 |  |
| Response length |  |  | 1000 |
