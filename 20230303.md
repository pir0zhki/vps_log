# OS再インストール
参考：https://doudonn.com/saba/2072/
## インストールについて
ポート番号変更なし(22のまま，変更する項目が見当たらず)<br>
ユーザ名：ubuntu<br>
パスワードはそのまま<br>
パスワード認証項目はなかった<br>
公開鍵は以前同様管理画面から登録(id_ed25519.pub)
## ssh認証について
キー：id_ed25519とid_ed25519.pub<br>
puttyやRlogin，TeraTermを使ってログイン成功後<br>
```
/etc/ssh/sshd_config
```
ファイルを編集し，以下の項目のコメントアウトを外したところ，接続できなくなった
```
PasswordAuthentication no
PubkeyAuthentication yes
```


## 試したこと
一旦上記の変更を元に戻し，パスワード認証を使いクライアントからsftpでid_ed25519.pubを送信<br>
ubuntu/と/etc/ssh/authorized_keysに置いてある状態<br>
クライアントから認証，[ログ](./etc/Putty_log)を見たところ前回と同じpasswd認証で通ってるっぽいので，おそらくsshd_configを編集しても変化がなさそうです。試してません。<br>
<br>
以上です。

## 解決
RSA/sshの設定をコマンドで実行
（ログで発覚）
22.04では未対応
ポートを開ける
→confを編集
