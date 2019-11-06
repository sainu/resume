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
ブログ | [さいぬのtechブログ](http://sainu.hatenablog.jp/)

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

#### 実績と取り組み

* デザイナーとプログラマー間でUIコンポーネントの粒度に対する認識を合わせるために[Storybook](https://storybook.js.org/)を導入しました。これにより、データロジックが関わらないUIコンポーネントのスタイル部分をデザイナーでもコミットができる体制になり、コミュニケーションコストを大幅に削ることができました。
* Nuxt.jsをGCPにビルド&デプロイするワークフローを[CircleCIのWorkflow](https://circleci.com/docs/ja/2.0/workflows/)で作成し、実際の開発者以外でもデプロイ&ロールバックができる体制を作りました。
* 既存のNuxt.jsはES6で書かれた部分が多く、私が改修する時にはVue.jsがTypeScriptを公式サポートした後でしたので、作り直しのタイミングで新しい技術構成でやるチャンスだと思い、Nuxt.jsをTypeScriptで書き直しました。

# 活動

## OSS

* [Modify method name in comment #1471 - yabwe/medium-editor](https://github.com/yabwe/medium-editor/pull/1471)
* [Update npm and grunt-autoprefixer #473 - orthes/medium-editor-insert-plugin](https://github.com/orthes/medium-editor-insert-plugin/pull/473)
* [Modify for missing markdown symbol #1200 - lynndylanhurley/devise_token_auth](https://github.com/lynndylanhurley/devise_token_auth/pull/1200)
* [Optimized for the latest version of npm packages #5 - Teddy-Zhu/vue-waves](https://github.com/Teddy-Zhu/vue-waves/pull/5)
* [show initial date #3 - tjohnn/vuejs-datetimepicker](https://github.com/tjohnn/vuejs-datetimepicker/pull/3)
* [add /app/jobs #12 - basyura/unite-rails](https://github.com/basyura/unite-rails/pull/12)
