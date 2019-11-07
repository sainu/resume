# [WIP] 職務経歴書

<img src="https://github.com/sainuio/resume/blob/master/img-profile2.jpg" width="128">

**"夢中は努力に勝る / 好きこそものの上手なれ"**

# 基本情報

Key | Value
--- | ---
Name | 道祖克理, さいぬ
Job | Webアプリケーションデベロッパー
Github | [@sainuio](https://github.com/sainuio)
Twitter | [@sainuio](https://twitter.com/sainuio)
Qiita | [@sainu](https://qiita.com/sainu)
ブログ | [さいぬのtechブログ](http://sainu.hatenablGog.jp/)

# 職務経歴

## 株式会社ティンク（2019年6月〜2019年8月）

### 美容整形口コミアプリのAPIサーバーパフォーマンス改善（2019年8月）

#### 概要
web、ios、androidから利用するAPIのレスポンス速度とサーバー負荷を軽減することを目的としたプロジェクト。

#### 業務内容

* サーバーログからボトルネックを特定
* 改善方針を立案
* 改修
* レスポンス速度&サーバー負荷テスト

#### 技術

* [Active Model Serializers](https://github.com/rails-api/active_model_serializers)

#### 実績と取り組み

* 当プロジェクトコードにおいて、モデルからJSONにシリアライズする際に使用するライブラリ（Active Model Serializers gem、以降AMS）の使い方に問題があり、重複データや不要なデータの多重ネストが起こっていたことを特定。JSONを再定義し、スナップショットテストを当エンドポイントに適用。負荷テストの後、数値比較をし、レスポンスサイズを1/2に、サーバーのスループットを1.8倍に、レスポンスタイムを1/2に改善しました。
* 同様の問題が起こらないようなライブラリの使い方をチーム内にナレッジで周知し、再発防止に努めました。

#### 振り返り

* AMSに対する理解:
AMS（バージョン0.10）のコードを追ってみると、各DSLは名前の通り「リソースの関連リソースとして定義する」と「リソースの属性として定義する」の違いがあることがわかりました。ライブラリがどんな思想で作られてるかを考えると、ActiveModelに似たインターフェースを持っていることから、このライブラリはView部分もRailsの思想同様にモデルと密に結合させることが良い使い方であることが理解できました。

### 美容整形口コミアプリのWebアプリケーションリニューアル開発（2019年6月〜2019年7月）

#### 概要
「SEO面の向上を目的にURL及びページ構成の再設計された新しい設計に合わせること」と「アプリに比べて遅れたデザインを最新のデザインに追いつくこと」を目的にWebアプリケーションを作り直すプロジェクト。

#### 業務内容

* Nuxt.jsを使ったWebアプリケーションの継続開発を想定した開発基盤の構築
* Nuxt.jsのWebアプリケーションを作り直し

#### 技術

* Nuxt.js
* TypeScript
* CircleCI

#### 実績と取り組み

* デザイナーとプログラマー間でUIコンポーネントの粒度に対する認識を合わせるために[Storybook](https://storybook.js.org/)を導入しました。これにより、データロジックが関わらないUIコンポーネントのスタイル部分をデザイナーでもコミットができる体制になり、コミュニケーションコストを大幅に削ることができました。
* Nuxt.jsをGCPにビルド&デプロイするワークフローを[CircleCIのWorkflow](https://circleci.com/docs/ja/2.0/workflows/)で作成し、実際の開発者以外でもデプロイ&ロールバックができる体制を作りました。
* 既存のNuxt.jsはES6で書かれた部分が多く、私が改修する時にはVue.jsがTypeScriptを公式サポートした後でしたので、作り直しのタイミングで新しい技術構成でやるチャンスだと思い、Nuxt.jsをTypeScriptで書き直しました。

## 株式会社ポケットペア（2019年3月〜2019年10月）

### ウェブサイト競合分析ツール開発（2019年5月〜2019年10月）

#### 概要
ウェブサイトを独自にカテゴライズし、ウェブサイトを分析するツールの開発

#### チーム構成
PM1人、デザイナー1人、エンジニア1人

#### 業務内容

* 機能企画
* 実装

#### 取り組み
機能の立案、ページ設計、情報設計、実装を行いました

#### 技術

* アプリケーション本体
  * Ruby on Rails（5系）
* クローラー
  * TypeScript
  * [Puppeteer](https://github.com/GoogleChrome/puppeteer)
  * [Faraday](https://github.com/lostisland/faraday)
* 開発環境
  * Docker
* DB
  * MySQL（5.7）
  * Redis
* 非同期処理
  * Sidekiq
* EC2
    * オンデマンド
    * スポットインスタンス
    * オートスケーリング
    * CloudWatch
* S3
* RDS

#### 技術的な振り返り

* 新規プロジェクト立ち上げでリリースまで素早く進める必要があり、インタラクティブ性の高い画面は要求されなかったので、フロントと管理画面はRailsの最小構成で作りました。
* クローラーは、定期的に短時間で大量のクロールを要求されるので、Redisに積まれたジョブ数をCloudWatchで測定し閾値を超えたらオートスケーリングでクローラーが起動するEC2スポットインスタンスの数を増やすことで、短時間で対象のクロールを処理するようなインフラ構成にしました。この構成の良いところは、インフラに関しての管理コードをCloudWatchにRedisのジョブ数を送信するだけのコード量で済む点です。こうすることで、メンテナンスをAWSに任せることができ立ち上げ当初のリソースをアプリケーションの開発に集中させることができました。のちに、AWS Loftの人にこの構成について聞いてところ、良い構成という評価を頂きました。

### 100人対戦ゲーム検証環境構築（2019年4月〜2019年5月）

#### 概要
100人同時接続ゲームを作る前に100人同時接続が可能かどうかを検証するための検証環境を構築。

#### 取り組み
バックエンドサーバー1台とヘッドレスクライアントサーバー99台を起動・停止・削除を簡単にできる必要があったため、ansibleを用いて1コマンドでそれらの操作をできるようにしました。

#### 技術

* ansible
* EC2（オンデマンド）

#### 技術的な振り返り

* ansible
  * EC2に対する状態変更を行うモジュールが組み込まれており、プロンプトでの対話による条件分岐ができるので、台数変更や状態をプログラムの変更なしに行うことができました
  * YAMLで振る舞いまで宣言していくので、プログラムで冪等性を書く必要がなくシンプルに記述ができメンテナンス性も高いと思いました
* EC2
  * 今回は納期の問題で使い慣れているオンデマンドを利用したプログラムを書いたが、後々にもう少し調査してみたところスポットインスタンスを利用した方が低いコストで検証ができたことがわかりました


## 株式会社デザート（分社化後 株式会社プレスブログ）（2017年8月〜2019年5月）

### 自社サービスプレスブログの開発（2017年8月〜2019年5月）

#### 概要
自社ブログサービス（プレスブログ）の開発

#### チーム構成
PM1人
デザイナー1人
最大エンジニア4人

#### 業務内容
新機能の設計、プロダクト開発チームのマネージメント、ウェブ開発、インフラのメンテナンス

#### 取り組み

* デザイナーと連携して新機能の画面設計を行い、実装・テストをしました。
* プロダクト開発チームのタスク進捗管理を行いました。
* iOSエンジニアと連携してAPI開発及びAPIドキュメントの作成を行いました。
* サイト内で使っているAngularJS1系を全てVue.js2系に書き換えました
* ブログ執筆画面をmedium-editorとそれの拡張でリニューアルしました
* 特にアクセスが集中するページをNginxでキャッシュしページ表示速度を向上及びサーバー負荷を軽減させより多くのトラフィックを処理できるようになりました

#### 技術

* アプリケーション
  * Ruby on Rails（4系）
  * Vue.js（2系）
  * AngularJS（1系）
  * Puma
  * Nginx
* DB
  * MySQL（5.6）
  * Redis
* サーバー
  * EC2（オンデマンド）
  * S3
  * RDS

#### 技術的な振り返り

* Nginxを使ったページキャッシュ
    * ブログという性質上、記事ページが一番閲覧されるのに投稿あたりの更新頻度は低く、DBやアプリケーションサーバーのリソースは、読み取りよりも書き込みや更新にリソースを使っていく必要があると考えました。なので、閲覧される割に更新頻度が低いページ（記事ページとプロフィールページ）に関しては、Nginx側でページをキャッシュを返すようにしました。この構成の欠点は、データの更新やレイアウトの変更が加わった時に、Nginxのキャッシュを削除する処理が必要という点でした。ただ、ページキャッシュをやる以上、どこでキャッシュしてもその処理は必要なので、ここではサーバーの負荷軽減を優先してページキャッシュを行いました。
* AngularJS→Vue.jsへ
    * ブログではGoogle botにクロールされる必要があるので、SPAという選択はありません。ただ、ページキャッシュをしている以上、コメントやユーザーによってコンテンツが変わる部分を動的に描画をする必要があります。当初AngularJS1系がJSのフレームワークで一番盛り上がっていた時期だったのでトレンドに合わせてこれを導入しましたが、AngularJS1系自体のファイルサイズの大きさによる動的コンテンツの読み込み速度の遅さがページの遷移の度に発生するので改善する必要がでてきました。Vue.jsがちょうどバージョン2にアップデートされた後で、ファイルサイズがかなり軽量でしたので、他のFWではなく、Vue.js2系を使うことにしました。実際、動的コンテンツの読み込み速度は、AngularJS1系を使っていた時の3倍程度早くなりました。

## 株式会社RUC（旧 株式会社ファーストペンギン）

### 自社サービスDROPPAの企画開発（2017年2月〜2017年3月）

#### 概要
Google Drive内のファイルを読み取り、最適なフォルダ構成を提案する士業向けのChromeブラウザの拡張機能を開発

#### チーム構成
デザイナー1人、エンジニア1人、PM1人

#### 業務内容
サービス企画、システム設計、実装

#### 取り組み

* ペルソナをもとに、サービスの機能とUIを設計
* システム設計と実装

#### 技術

* Chrome拡張（JavaScript ES5）
* Ruby on Rails（API only）

#### 技術的な振り返り

* Chrome拡張機能の開発は初めてで、ドキュメントを読みながらの開発になりました。manifestファイルとchromeオブジェクトの振る舞いをドキュメントでしっかり把握することがChrome拡張機能の開発の上で一番重要なことでした。

### Webサイト制作受託業務（2016年12月〜2017年1月）

#### 概要
Wordpressを使ったWebサイト制作の受託開発

#### チーム構成
デザイナー1人、エンジニア1人、PM1人

#### 業務内容

* サーバー構築及び運用
* Wordpressのカスタムテンプレート作成

#### 取り組み

* さくらのレンタルサーバーでwordpressの運用
* Wordpressのカスタムテンプレートを作成

#### 技術

* Wordpress

# スキル

* 言語
  * Ruby（2.1系 / 2.2系 / 2.5系 / 2.6系）：2015年7月〜現在
  * JavaScript（ES5 / ES2015 / ES2016 / ES2017）：約2015年7月〜現在
  * Node.js（6.x系 / 8.x系 / 10.x系）：2016年2月〜現在
* フレームワーク
  * Ruby on Rails（4系 / 5系）：2015年7月〜現在
  * Vue.js（2系）：2017年9月〜現在
  * AngularJS（1系）：2016年6月〜2017年1月
  * Chrome extension：2017年2月〜2017年3月
* DB
  * MySQL（5.6 / 5.7）：2015年7月〜現在
  * Redis：2017年8月〜現在
* ミドルウェア
  * Nginx：2017年8月〜現在
* DevOps
  * ansible：2019年4月〜2019年5月
* AWS：2016年2月〜現在
  * EC2（オンデマンド・スポットインスタンス）
  * S3
  * ALB
  * オートスケーリング
  * SES
  * CloudWatch
  * RDS（MySQL5.6,5.7）
  * Elasticache（Redis）
  * Elasticsearch Service

# 活動

## OSS

* [Modify method name in comment #1471 - yabwe/medium-editor](https://github.com/yabwe/medium-editor/pull/1471)
* [Update npm and grunt-autoprefixer #473 - orthes/medium-editor-insert-plugin](https://github.com/orthes/medium-editor-insert-plugin/pull/473)
* [Modify for missing markdown symbol #1200 - lynndylanhurley/devise_token_auth](https://github.com/lynndylanhurley/devise_token_auth/pull/1200)
* [Optimized for the latest version of npm packages #5 - Teddy-Zhu/vue-waves](https://github.com/Teddy-Zhu/vue-waves/pull/5)
* [show initial date #3 - tjohnn/vuejs-datetimepicker](https://github.com/tjohnn/vuejs-datetimepicker/pull/3)
* [add /app/jobs #12 - basyura/unite-rails](https://github.com/basyura/unite-rails/pull/12)

## 受賞

* 2016/12/13: [マイナビ主催 IoTハッカソン 総合2位&企業賞](https://www.facebook.com/sainou.katsutoshi/posts/1889658084601848?__xts__[0]=68.ARCDxIHnlLxUdr1qF_hfbxO6cxX2A3bX78p6ND4S08GpBII7lQEvh7vwQ0OQkM3Ug2vvooTT76Mrd9UMMuVvFTigIkdyFaifO1PR6Nk2PfkZN5lV1dFZ4fYml3nKSmiEwhsMa3bg7Wy9OzUBatv8lPCdFb3gMUOozJ2yLxAzbo_Yv97zgK_L-gqB9ylCidgbgtSHCtWMUc0mu0IL7jQeKylG50jFxhl7L-ZSlB0P5GSDTpwzVav_PFLSONL6U6id6QNa6g2f_Pr-TokpM-jm0toKXL_haDdZ-rFq8QCZvrkQBCkwVtdxFThU0qRUF35dTRu5grtU77iTxSvZwxNNqUusPg&__tn__=-R)
