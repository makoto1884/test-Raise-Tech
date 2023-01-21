# 第３回提出用課題  
***１.*** 通信関係の動画視聴  

***2.*** ubuntuを使用したrailsインストールと実行（失敗）  
>あとでわかったが理由はセキュリティーグループのポート番号が原因  

***3.*** amozon linuxの構築に変更  
>（ubuntuを使用していなかった、基礎的な理解をしたかった）  

***4.*** bundleの理解と使用方法  

***5.*** rbunvを使用したruby install  

***6.*** rails install  

***7.*** mysql install pass設定と動作確認  
>installの際 Nothing to do と言われたため  
>wget コマンドで rpm パッケージを Amazon >Linux2 のローカルにダウンロードして実行  
>wget コマンドを使用して MySQL の RPM パッケージをダウンロード→rpm パッケージをインストール>>する
>→MySQL クライアント機能をインストール→バージョ>ン確認の順で実行




***8.*** rails newコマンドでmysqlをdbに指定して作成  

***9.*** mysql-devel mysql2のinstall  
>エラーが発生してmysqlをdbとして  
>使用できない状態  
>mysql-develをyumでinstallしてgemでmysqlをinstall（Gemfileにすでにある為bundle install）  

***10.*** rails sの実行
>理由としてec2のセキュリティーグループにport番号 3000番を追加していなかった為 追加  

***11.*** databese.ymlにmysql user/passを追加  
>アクセスできる環境になったが  
>エラーが発生mysql2のuser/passwordを確認してと表示  
>調べた結果 Config/detabase.yml内のusernameとpasswordを設定してほしいとのこと  
>mysqlにログインし別ユーザーを作成  
>権限はすべてできる設定  
作成後 databese.ymlにユーザー名とパスワードを記載  

***12.*** rails db:createの実行  
>再度 rails sを実行したが失敗  
>次はデータベースを作りましたか？と聞かれた為  
rails db:createを実行し
>再度rails s→成功

7番から１２番はかなり手間取りました！
