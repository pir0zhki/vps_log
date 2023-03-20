# 1.ローカル環境にBasic認証を導入(動作確認)
### ベーシック認証
参考：https://www.itra.co.jp/webmedia/basic_authentication.html<br>
### Apacheローカル環境構築
参考：https://picosy.jp/wp/local-http-server-intro-apache/<br>

## 躓いたところ
### Apacheが起動しない
原因：Apacheが使用するポート番号80をWindowsのSystemがを使用しているため
```
netstat -nao
```
でローカルアドレスが:80となっている項目のPIDの番号を探す<br>
タスクマネージャで詳細タブを開き，先程のPIDの番号と一致する項目を探し<br>
タスクの終了をする<br>

起動方法はタスクマネージャのサービスタブなど<br>

参考:http://lovee7.blog.fc2.com/blog-entry-35.html

### 再起動忘れ
タスクマネージャから再起動<br>
変更を加えたら必ず再起動する<br>



### ダイアログが表示されない<a id="ps"></a>
httpd.confを編集して解決<br>
・Require all grantedをコメントアウト(すべてのユーザを通す的な文言)<br>
・AllowOverride None→Allに変更<br>

参考：https://marketing-wizard.biz/blog/server/basic-htaccess/

# 2.サーバのwebページにBasic認証を実装
ローカル環境で作成したファイルを移動させたがwebページ自体が表示されず<br>
調べると一般的な実装方法が結構違ったので１から作成<br>
参考：https://beyondjapan.com/blog/2022/09/apache_basic_auth/#basic-2
## 500 Internal Server Errorの解決
webページが表示されず，上記のエラー表示

### 原因：パスをフルパスで書いていなかった
```
/etc/apache2/sites-available/transcription.conf
```
```
/var/www/transcription/.htaccess
```
上記2つに記述したパスを下記に変更
```
/home/ubuntu/var/www/transcription
```
参考：https://pointsandlines.jp/server-infra/basic-authorize<br>

webページは表示されるがダイアログが出ず。。<br>
## ダイアログが出ない問題、試したこと
### .htaccessファイルの最後に空行１行加える
必須だった
### Apacheの再起動
```
sudo systemctl restart apache2
```
で毎回再起動しました
### ファイルの権限を604から644に変更する
他の条件を変更する度に実行
### .htaccessファイルのパスの""を消す
### /を\に変えてみる
.htpassファイルのパスの記述に問題があるのではないかと思って実行<br>
変化なし
### プライベートブラウズモードで確認
既に認証が済んでいるかもしれないと思って実行<br>
変わらず<br>

参考： https://lmn-blog.com/htaccess01/
## 他の可能性
・全角が含まれてしまっている<br>
・httpd.confファイルを探して [ローカル同様](#ps)の編集を行う<br>
(httpd.serviceが存在しない代わりに，apache.serviceという機能があるらしく，
httpd.confファイルと同等のファイルを探して編集することが考えられる)<br>

## 解決?
- 全てのpathをフルパスで記述するように書き直したらできた


















