# vps_bug_ssh.pub

コンソール
C:\Users\coral\.ssh>ssh -v -l linuser -i id_rsa 153.120.41.188
ログ付きでサーバに接続しまーす

Connecting to 153.120.41.188 [153.120.41.188] port 22.
Connection established.

Local version string SSH-2.0-OpenSSH_for_Windows_8.1
ローカル バージョン文字列 SSH-2.0-OpenSSH_for_Windows_8.1

Remote protocol version 2.0, remote software version OpenSSH_8.9p1 Ubuntu-3ubuntu0.1
リモート プロトコル バージョン 2.0、リモート ソフトウェア バージョン OpenSSH_8.9p1 Ubuntu-3ubuntu0.1
*サーバ側の情報を入手？

match: OpenSSH_8.9p1 Ubuntu-3ubuntu0.1 pat OpenSSH* compat 0x04000000
一致

 Authenticating to 153.120.41.188:22 as 'linuser'
 「linuser」として 153.120.41.188:22 への認証
  
 kex: algorithm: curve25519-sha256
 kex: host key algorithm: ecdsa-sha2-nistp256
 kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
 圧縮なし
 kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
 
 expecting SSH2_MSG_KEX_ECDH_REPLY
 期待
 SSH2_MSG_NEWKEYS received
 受け取りました
 
 Server host key: ecdsa-sha2-nistp256 SHA256:cvfmBW3/z643nV7ed+meqY1W4YhGgYr1xTrH1hjmzOA
 Host '153.120.41.188' is known and matches the ECDSA host key.
 ホスト '153.120.41.188' は既知であり、ECDSA ホスト キーと一致します。
 
 Found key in C:\\Users\\coral/.ssh/known_hosts:2
 
 rekey out after 134217728 blocks
 134217728 ブロック後にキーを再生成する
 
 SSH2_MSG_NEWKEYS sent
 送った
 expecting SSH2_MSG_NEWKEYS
 期待する
 SSH2_MSG_NEWKEYS received
 受け取った
 
 rekey in after 134217728 blocks
 134217728 ブロック後に再キー入力
 
 
 ##pubkey_prepare: ssh_get_authentication_socket: No such file or directory
 ##pubkey_prepare: ssh_get_authentication_socket: そのようなファイルまたはディレクトリはありません
 公開鍵の準備
 
  Will attempt key: id_rsa RSA SHA256:n7eS/kbemIo6arCgtJB9AGzf6JOw5qEsCo61eq4O8f0 explicit
 キーを試行します: id_rsa RSA SHA256: n7eS / kbemIo6arCgtJB9AGzf6JOw5qEsCo61eq4O8f0 明示的
 
 SSH2_MSG_EXT_INFO received
 
 kex_input_ext_info: server-sig-algs=<ssh-ed25519,sk-ssh-ed25519@openssh.com,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ecdsa-sha2-nistp256@openssh.com,webauthn-sk-ecdsa-sha2-nistp256@openssh.com>
 
  kex_input_ext_info: publickey-hostbound@openssh.com (unrecognised)
 (認識されない)
 
 SSH2_MSG_SERVICE_ACCEPT received

Authentications that can continue: publickey
継続できる認証: publickey
Next authentication method: publickey
 次の認証方法: publickey

Offering public key: id_rsa RSA SHA256:n7eS/kbemIo6arCgtJB9AGzf6JOw5qEsCo61eq4O8f0 explicit
公開鍵の提供: RSA id_rsa SHA256: n7eS / kbemIo6arCgtJB9AGzf6JOw5qEsCo61eq4O8f0 明示的
*RSA:公開鍵の暗号方式

 Authentications that can continue: publickey
 継続できる認証: publickey
 
  No more authentication methods to try.
 もう認証方法を試す必要はありません。
 
 linuser@153.120.41.188: Permission denied (publickey).
 linuser@153.120.41.188: 許可が拒否されました (公開鍵)。
 
