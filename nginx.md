# nginx
## yumのinstall
- リポジトリ追加
  - `vi /etc/yum.repos.d/nginx.repo`
  - 中身は[https://qiita.com/witchcraze/items/64663ec9c7981f4021d6]参照
- install
  - `yum --disablerepo=AppStream install -y nginx`

## 各種設定
- 設定ファイル
  - `/etc/nginx/nginx.conf`
- 公開ディレクトリ
  - `/usr/share/nginx/html`
  設定ファイルのserverに書いて変更可能（restart必須）

## ASP.NET導入
- Linuxにインストール
  - `dnf install dotnet-sdk-3.1`
- VisualStudioがあるパソコン上で発行(csprojに移動)
  - `dotnet publish --configuration Release`
- Linuxに発行した中のpublishフォルダの中身を移動
- 移動先でdotnet [システム名]dllで起動
