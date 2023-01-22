1. rvm get head  
>最新の状態にアップロード
2. rvm list kwon  
>ダウンロードできるものをリスト化  
3. rvm install  指定ruby  
>3.1.2を使用  
>rvm関連  
<https://blackhawk888.github.io/blog/2018/01/22/rvm-version-switch/>  

4. bundler -v  
>バンドルのバージョン確認
5. bundle install  
>ファイル等をアップロードする（最新状態にする）  

6. datebase.yml 作成  
>config内のdatebase.yml.sampleをdatabase,ymlにコピー  
>コピー完了後database.ymlにmysqlの>rootpassを入力  

7.bundle関係について
>bundle installとbundle execの違い
>詳細URL
<https://pikawaka.com/rails/bundler>

>bundle install  
>bundle installとは、bundlerを使ってGemfileからgemをインストールするコマンド。  
>以下を実施する  

- Gemfile.lockでどのgemがinstallされているか確認する  

- Gemfile.lockを確認した後にGemfileに記述されているgemを確認する  

- Gemfile.lockにないgemをGemfileから見つけた場合、そのgemをインストールする。  

>bundle execコマンドはrailsアプリでインストールしたgemを指定して読みこんでくれる。  
>bundle execコマンドを使用  
>しなければシステム共通の  
>ライブラリ保存場所を環境下にしてコマンドが実行されるので、bundle installでinstallしたgemのバージョンでないgemを使用する  
>可能性があり結果としてgemが動かなくなる可能性がある。

8. mysqlソケット場所確認URL 
<https://www.tweeeety.blog/entry/2015/07/11/183505>  

>budle exec rails db:create
を実行したいがmysqlのソケットがないと言われる為 installする。  
>datebase.ymlのdevelopmentとtestのsoketを書き換える

9. bundle exec rails db:createと
migrateを行う  
<https://qiita.com/windhorn/items/0f58866291f8273f18fb>  

## db:createやdb:migrateの記述  
### create  
>このコマンドを実行すると，Railsプロジェクトのconfigディレクトリの中にあるdatabase.ymlを読み込み，そのファイルに基づいてデータベースを作成する  

### migrate  
>このコマンドを実行すると，Railsプロジェクトのdb/migrateディレクトリの中にあるスクリプトファイルに基づいてデータベースにテーブルを作成する。

10.rails sの実行
### bundle exec rails s -b 0.0.0.0の実行  

>失敗 理由としてrailsのセキュリティー上設定しないと開けないようにしている為。
>まずポート番号の設定  
セキュリティーグループのインバウンドルールからポート8080の設定とhttpの設定を実施 実行→失敗
rails側の記述を変更してと出る
profile.devの設定がポート番号3000の設定になっている為 以下に変更  
>web: bin/rails server -p 8080 -b 0.0.0.0  
>再び実行→失敗
必要なアプリケーションがないと表示された。  

11. yarnをinstall  
>npm install -g yarn  
>インストール後yarn installを実施

<https://e-words.jp/w/Yarn.html>  

>Yarnとは、主にJavaScriptで開発されたプログラム部品（モジュール）を管理するためのパッケージ管理システムの一つ。npmと互換性があり、乗り換えたり併用することができる。
JavaScriptプログラムに組み込んで機能を追加するパッケージの管理を行うためのシステムで、公開されているパッケージの検索や入手、手元の環境への導入、不要になったパッケージの削除などを行うことができる。  
>Node.js向けに開発された有力なパッケージマネージャであるnpm（Node Package Manager）と同じpackage.json形式のパッケージを扱うよう設計されており、npmの代わりとして利用することができる。  
>再び起動→失敗

12. manifest.jsの２行目を削除
>app→configのmanifest.js内の２行目を削除。  
>起動→成功








