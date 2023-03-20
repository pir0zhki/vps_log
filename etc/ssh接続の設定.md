# 20230303 さくらVPS(ubuntu22.04)へのSSHー接続

## 実施手順

### 新規ユーザ(SSH-RSA接続用)の作成

サーバに ubuntu(root)ユーザ&パスワード認証でログイン

#### 新規ユーザ(ここではshamrock)の作成
$ sudo adduser shamrock  

#### shamrock を sudo グループに追加
$ sudo gpasswd -a shamrock sudo  

### rsa認証の公開鍵/秘密鍵の作成と配置

#### クライアント側の端末の SSH クライアントで rsa認証の公開鍵/秘密鍵を作成

この作業内容は以下のサイトの「公開鍵と秘密鍵の作成」を参照  
https://manual.sakura.ad.jp/vps/support/technical/ssh-ch.html#id10

#### 作成した 公開鍵を サーバ側(ユーザのホームディレクトリにアップロード

この作業内容は以下のサイトの「公開鍵認証の設定」を参照  
https://manual.sakura.ad.jp/vps/support/technical/ssh-ch.html#id4

#### shamrock ユーザのホームディレクトリに移動し公開鍵認証の設定を実施

##### ホームディレクトリに .sshフォルダ を作成しフォルダの権限を700に変更
$ mkdir .ssh  
$ chmod 700 .ssh  

##### 公開鍵ファイル(id_rsa.pub)の中身をcatコマンドでauthorized_keysファイルに出力&保存
$ cat id_rsa.pub > .ssh/authorized_keys 

catコマンドでできることはこちらを参照のこと  
https://eng-entrance.com/linux_command_cat

##### authorized_keys ファイルの権限を 600 に変更  
$ chmod 600 .ssh/authorized_keys  

##### 元の公開鍵ファイルを削除
$ rm -f id_rsa.pub  

### SSH通信の設定

ここで ubuntu(root) ユーザで再ログイン

#### sshの設定が記述されている sshd_configファイルの記述内容を変更

vi エディタで当該ファイルを開く(変更し保存できるようにsudoで開く)

$ sudo vi /etc/ssh/sshd_config  

##### コメントアウトされているポートのハッシュを外してport22の通信を有効にする
before:  
$ #Port 22  

after:  
$ Port 22  

##### 公開鍵認証を有効にする
before:  
$ #PubkeyAuthentification yes 

after:  
$ PubkeyAuthentification yes 

##### ssh-rsa 認証を有効にする
以下を追記：  
$ PubkeyAcceptedAlgorithms=+ssh-rsa  

### SSH Server が実行されているか確認
$ sudo systemctl status ssh

### RSA認証によるSSH通信をしてみる

この作業内容は以下のサイトの「公開鍵認証でのログイン方法」を参照 
https://manual.sakura.ad.jp/vps/support/technical/ssh-ch.html#id6
