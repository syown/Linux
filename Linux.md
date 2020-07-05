# Linux
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
- rootでのログインを禁止
  - `PermitRootLogin no`
- ポート番号変更
  - `Port 29537`
- firewallでsshを削除しポート29537を追加
 
### エラー
- SElinuxがONだとポート番号の変更を行うことができない
  - 状態確認:`getenforce`
  - オフ:`setenforce 0`
  - これだと一時的で起動のたびに設定する必要がある。
  - `vi /etc/selinux/config`
  - SELINUXのenforcingをdisableに変更
  - `reboot`しないと反映されない

## 権限
- `ls -l`で権限確認
- ファイル、フォルダの権限
  - `chmod [777] [ファイル名]`

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

## httpd
- https://www.linuxacademy.ne.jp/lablog/infrastructure/532/
