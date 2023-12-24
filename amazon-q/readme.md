## Amazon Qに関する情報

- 業務での利用に特化し、お客様のビジネスに合わせてカスタマイズできる新しいタイプの生成系 AI アシスタント
- セキュリティとプライバシーを念頭に置いて構築された新タイプの生成系 AI アシスタントにより、社内のデータと専門知識を利用して、質問への回答、問題の解決、コンテンツ作成、行動を起こすことが可能に
- **Amazon Qの特徴**：Amazon Qは、お客様のビジネスに合わせてカスタマイズできる生成系AIアシスタントで、社内のデータやシステムにアクセスして、質問に回答したり、コンテンツを作成したり、アクションを提案したりできます。Amazon Qは、セキュリティとプライバシーを重視して設計されており、お客様のコンテンツを基盤モデルのトレーニングに使用しません。
- **Amazon Qの利用方法**：お客様は、AWS Management Console、ドキュメンテーションページ、IDE、Slackなどから、自然言語でAmazon Qに質問したり、依頼したりできます。Amazon Qは、AWSのサービスや機能に関する知識やベストプラクティスを持っており、アプリケーションやワークロードの構築、デプロイ、運用を支援します。また、Amazon Qは、お客様のビジネスデータや情報、システムに接続できるため、業務に関連したインサイトやコンテンツを提供できます。
- **Amazon Qの展開先**：Amazon Qは、Amazon QuickSight、Amazon Connect、AWS Supply ChainなどのAWSのサービスやアプリケーションに統合されており、生成系AIによる支援を提供します。お客様は、これらのサービスやアプリケーションを使って、ダッシュボードやレポートの作成、コンタクトセンターの対応、サプライチェーンの分析などを行うことができます。
- **Amazon Qの利用状況**：Amazon Qは現在プレビュー版がお客様に提供されていますが、Amazon Q in Connectは一般利用可能で、Amazon Q in AWS Supply Chainは近日中に一般提供が開始される予定です。

### 詳細はこちら
- Amazon Q Developer Guide
    - AWS
    - https://docs.aws.amazon.com/amazonq/latest/business-use-dg/what-is.html
- AWS、未来の働き方の概念を変える Amazon Q を発表
    - AWS
    - https://aws.amazon.com/jp/about-aws/whats-new/2023/12/aws-announces-amazon-q-to-reimagine-the-future-of-work/
    - 投稿日: Dec 13, 2023
    - サービスについての詳細が記載されている
- Amazon Q が、IT 専門家やデベロッパーに生成系 AI を活用した支援を提供 (プレビュー)
    - AWS
    - https://aws.amazon.com/jp/about-aws/whats-new/2023/12/aws-announces-amazon-q-to-reimagine-the-future-of-work/
    - 投稿日: Dec 13, 2023
    - 使い方がスクショも交えながら記載されている
- ****AWS、業務での利用に特化しビジネスに合わせてカスタマイズできる生成系AIアシスタント「Amazon Q」を発表****
    - 日本経済新聞
    - https://www.nikkei.com/article/DGXZRSP665820_U3A211C2000000/
    - 2023年12月14日 10:31
    - 特に新しい情報はないが、簡潔にまとまってる
- **新サービス Amazon Q（ビルダー向け）のドキュメントを総なめして、できることをざっくり把握する #AWSreInvent**
    - [濱田孝治](https://dev.classmethod.jp/author/hamada-koji/)
    - https://dev.classmethod.jp/articles/amazon-q-builder-user-docs/
    - 2023.12.01
 
## Amazon Qを使用してみる
- amazon qについての質問
    - 答えてくれない
    ![aq1](https://github.com/dx-junkyard/opendata-bridge-research/assets/69392748/faf9e1d1-46ca-42cb-beed-764c9837073b)
- ブレインストーミングを行わせてみる
    - 回答はしてくれる
    ![image](https://github.com/dx-junkyard/opendata-bridge-research/assets/69392748/9d292af6-1525-4434-ab15-55992a1877f1)


## RAGを使用する
- 論文データ
    - 答えてくれた 
    ![aq2](https://github.com/dx-junkyard/opendata-bridge-research/assets/69392748/6f62d6de-7b67-4b20-b4c5-e44dcc94182e)

- 北九州市のデータ（令和5年度　北九州市税務統計　税外収入）：
    - うまくいかない。
    ![image](https://github.com/dx-junkyard/opendata-bridge-research/assets/69392748/382d013c-9d7b-4a98-90c6-d89bde97d152)

## 上記に関する補足
- Amazon Qは日本語非対応であることから、いくつかの点でうまく文章を生成できていない可能性を確認した
    - 2023年12月24日現在

## 候補として
- 現在としては、やめておいた方が良いかもしれない

### 参考

- Amazon Q の情報まとめ & 触ってみた (2023/12/1時点)
    - yuki_ink（AWS re:Invent 2023 参加者）
    - [https://qiita.com/yuki_ink/items/48ee6cffbf691b3712](https://qiita.com/yuki_ink/items/48ee6cffbf691b3712c6)
    - 最終更新日2023年12月02日　投稿日 2023年12月02日
