# RDSの構築とEC2への接続  

VPCやEC2インスタンスに関しては事前に学習と理解がある程度終わっていたため課題提出の際は復習程度のレベルですので割愛させていただきます。  

1 RDS専用のセキュリティグループ作成  

2 プライベートサブネットを作成  
>dbsubnetグループを作成するためには
>異なるプライベートサブネットが必要。  
>今回の場合 AZ  
**ap-northeast-1a**  
**ap-northeast-1c**を使用  
サブネットのCIDRは異なる設定を実施。  

3. RDSのサブネットグループを作成  
>vpcはメインvpc  
>subnetはプライベートサブネットを２つ定義  

4. パラメーターグループとオプショングループを設定。

5. mysqlのRDSインスタンスの作成  
> - 作成方法は「標準作成」  
> - エンジンは「MySQL」  
> - バージョンは8.0.28を選び
テンプレートは「無料利用枠」  
> - DBインスタンス識別子を設定後  
> - マスターユーザー名、パスワードを登録  
> - DBインスタンスサイズはdb.t2.microを選択  
> - 「ストレージの自動スケーリングを有効にする」のチェックを外しておく  
> - 「接続」では、作成済みのVPCを割り当て  
> - サブネットグループは作成したグループを割り当て  
> - セキュリティーグループではインバウンドルールにmysql通信を許可した
ポート番号を割り当て  
> - AZはap-northeast-1aを割り当て  
> - データベースポートは3306  
> - パラメーターグループとオプショングループを設定して作成  

6 ec2-userでmysqlをダウンロード  
```
sudo yum -y install mysql
```
7 ec2からRDSへ接続
```
mysql -h エンドポイントURL -u ユーザー名 -p→失敗
```
8 問題の追求と対応  
>問題は３つ考えられると推定  
> - セキュリティーグループの設定ミス  
> セキュリティグループsourceをwebserverで使用していたのが原因と推定  
> ググってmysqlのセキュリティグループを作成したグループに設定  

> - user.passミス  
> 可能性の一つとして考えた為、再度作り直しRDSとの疎通を確認  
```
curl -v telnet://[RDSインスタンスのエンドポイント]:[ポート番号]  
```
> - 接続時のコード記載  
> ポート番号を指定する記述の方が確実と考え変更  
```
mysql -h mysql–instance1.123456789012.us-east-1.rds.amazonaws.com -P 3306 -u mymasteruser -p  
```
再度実行→成功


参考サイト
- [RDSインスタンス作成](https://100webdesign.jp/services/web_knowhow/aws-site/web_knowhow-21162/)  
- [RDS疎通確認](https://oji-cloud.net/2019/10/04/post-3184/)
- [ログインコマンド](https://docs.aws.amazon.com/ja_jp/AmazonRDS/latest/UserGuide/USER_ConnectToInstance.html)
