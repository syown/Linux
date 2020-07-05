# AWSについて
Amazonが提供しているクラウドサービス
サービスがめちゃくちゃ多いが使うのは多分少しだけ
## AmazonEC2
- 基本的にサーバーを立てるならこれ
- firewallが入っておらずaws上のセキュリティグループでportの制御を行う
- SELinuxなどのいらないシステムもちゃんと設定してあり、手間がいらない

## Elastic Beanstalk
簡単にデプロイが可能になる

# EC2でのサーバー構築
## インスタンスの作成
- 今回は無料枠なのでRed-hat32bitのt2-microでの構築

## nginx
- インストール
  - `sudo amazon-linux-extras install nginx1.12 -y`
- 起動
  - `sudo systemctl start nginx`

これだけでnginxのページがたってしまう(AWS恐ろしや)
