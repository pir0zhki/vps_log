# Apacheのインストール
### Apacheの再インストール
手順は以下のサイトの「Apacheのインストール」<br>
参考:https://elec-hobby.com/vps-vol-03-apache/#toc4
# SSH認証続き
## authorized_keysにRSAで作成したキーを追加
TeraTermでパスワード認証でログイン後にD&D<br>
catで移動して追加

```
cat id_rsa.pub >> .ssh/authorized_keys
```

## SFTPでwebサイトをサーバにコピー
### ローカルのターミナルからsftp接続
```
sftp ubuntu@153.xxx.xxx.xxx
```
### sftpで接続後以下のコマンドでディレクトリごとコピー

```
put -r transcription
```
/home/ubuntu/から/var/www/に移動<br>
参考:https://dezanari.com/ssh-sftp/#toc4
### VirtualHostの設定
手順は以下のサイトの「仮想ホストの設定」部分<br>
https://elec-hobby.com/vps-vol-03-apache/#toc8<br>
前回同様上手くいかず，/etc/apache2/sites-availabale/内の<br>
000-default.conをローカルにコピーした後，消去して再起動，表示される<br>
参考:(./20230228.md)

#### jsonファイルのパースエラーについてのメモ
コンソールに以下のerror<br>
_unexpected character at line 1 column 1 of the JSON data_<br>
jsonファイルには問題なし<br>
ローカルでは問題がなく，ローカルのapacheサーバを使うとjson読み込まず<br>
transcription/script/index.jsのdata.page_path部分をパスに置き換えると上手くいった<br>
jsonのpage_pathを./page1.htmlからurl(http://localhost/...)に変更して成功

