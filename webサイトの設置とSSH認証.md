# webサイトの設置とSSH認証続き
## webサイト設置(完了)
### 手順
```
startx
```
でGUIに切り替え<br>
GoogleDrive上に置いたwebサイト(transcription)をダウンロード<br>
/var/www/に保存<br>
transcription.confを作成しrootを<br>
/var/www/transcription<br>
とした<br>
以前のconfファイルを消去して，transcription.confを有効化<br>
<br>
成功。
## SSH接続
https://super-vitality.com/ssh-setuzoku/ <br>
を基に実施

## 試してみたこと
すべての工程の後で再起動・chmodでパーミッションを600(または400)に変更
### 公開鍵は前回のままでパスを変更
前回windowsで作成した鍵のペアで実行<br>
_(1).ssh/authorized_keys_<br>
authorized_keysはファイル<br>
authorized_keysの中に公開鍵(id_rsa.pub)をペースト<br>
→接続できず<br>
<br>
_(2).ssh/authorized_keys/id_rsa.pub_<br>
_(3).ssh/id_rsa.pub_<br>

(2)のauthorized_keysはディレクトリ<br>
GUIでの操作を通してid_rsa.pubを移動<br>
→接続できず<br>
### wslで鍵のペアを再作成
wslのubuntu-22.04で実行<br>
前回windowsで作成した鍵は一旦サーバ側から削除し<br>
同じ名前で作成(id_rsaとid_rsa.pub)<br>
### 試したパス(1)
クライアント側の秘密鍵のパス:linux/ubuntu-22.04/home/coral/.ssh<br>
サーバ側に置いた公開鍵のパス:ubuntu/.ssh/id_rsa.pubと.ssh/authorized_keys/id_rsa.pub<br>
→接続できず<br>
### 試したパス(2)
クライアント側の秘密鍵のパス:<br>
linux/ubuntu-22.04/home/coral/.ssh<br>
サーバ側に置いた公開鍵のパス:<br>
home/coral/.ssh/id_rsa.pubとhome/coral/.ssh/authorized_keys/id_rsa.pub<br>
→接続できず<br>
### 解決
- SSH接続関係の問題はubuntu22.04が標準でRSAに未対応であったことに起因
- 別ページで記述













