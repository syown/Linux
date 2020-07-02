# 自宅サーバー公開への道
## 実行環境

| 名称 | ip |
|------|------|
|ルーター|192.168.0.1|
|メインpc|192.168.0.8|
|サーバー|192.168.0.4|

## ネットワーク内に公開する方法

- ゲストOS上の `/var/www/html/`にhtmlを配置する。(デフォルト)
- ネットワークアダプタをブリッジに変更

## ネットワーク外に公開する方法
- ルーター(192.168.0.1)のDMZホスト設定をする

## ポート番号変更方法
- /etc/httpd/conf/の中のhttpd.confを編集
  - `cd /etc/httpd/conf`
  - `vi httpd.conf`

## Apache起動
- `systemctl start httpd`
- `systemctl restart httpd`

## Linux システム 自動起動
- 状態確認
  - `systemctl is-enabled [システム名]`
- 自動起動
  - `systemctl enable [システム名]`

## ファイアーウォール設定
- 現在のゾーン
  - `firewall-cmd --get-active-zones`
- ゾーンに許可するシステムを追加
  - `firewall-cmd --add-service=[システム名] --permanent`
- ゾーンごとに許可されてるシステムを確認
  - `firewall-cmd --list-all-zones`
- 更新
  - `firewall-cmd --reload`

## SSH接続
- 設定フォルダ `/etc/ssh/sshd_config`
### 設定内容
- rootでのログインを禁止
  - `PermitRootLogin no`
- ポート番号変更
  - `Port 29537`
 
## エラー
- SElinuxがONだとポート番号の変更を行うことができない
  - 状態確認:`getenforce`
  - オフ:`setenforce 0`
  -これだと一時的で起動のたびに設定する必要がある。
  - `vi /etc/selinux/config`
  - SELINUX=enforcingをdisableに変更
  - `reboot`しないと反映されない

## 権限
- `ls -l`で権限確認
- ファイル、フォルダの権限
  - `chmod [777] [ファイル名]`


## ログ
- エラーログの場所
  - /var/log/httpd/access_log

## MariDB

- MariaDBのインストール
  - `yum -y install mariadb mariadb-server`
- 初期設定
  - `mysql_secure_installation`
- ログイン
  - `mysql -u root -p`

## PHP

- phpのインストール
  - `yum -y install php php-mbstring php-mysqli`
- PHP設定ファイル
  - /etc/php.ini

# 参考

## おおまかなまとめ
- http://changineer.info/server/virtualization/virtualbox.html#_8211-5

## ネットワークのつなぎ方
- https://qiita.com/kamonegi/items/965a8519c6126b6c90ce

## インターネットアダプターについて
- https://ponsuke-tarou.hatenablog.com/entry/2017/06/14/001009
- http://zorinos.seesaa.net/article/439666371.html#target3

- $ sudo systemctl restart NetworkManager.service

## httpd
- https://www.linuxacademy.ne.jp/lablog/infrastructure/532/


a