# vps_bug_ssh.pub

コンソール
C:\Users\coral\.ssh>ssh -v -l linuser -i id_rsa 153.120.41.188<br>
ログ付きでサーバに接続しまーす<br>

Connecting to 153.120.41.188 [153.120.41.188] port 22.<br>
Connection established.<br>

Local version string SSH-2.0-OpenSSH_for_Windows_8.1<br>
ローカル バージョン文字列 SSH-2.0-OpenSSH_for_Windows_8.1<br>

Remote protocol version 2.0, remote software version OpenSSH_8.9p1 Ubuntu-3ubuntu0.1<br>
リモート プロトコル バージョン 2.0、リモート ソフトウェア バージョン OpenSSH_8.9p1 Ubuntu-3ubuntu0.1<br>
*サーバ側の情報を入手？<br>

match: OpenSSH_8.9p1 Ubuntu-3ubuntu0.1 pat OpenSSH* compat 0x04000000<br>
一致<br>

 Authenticating to 153.120.41.188:22 as 'linuser'<br>
 「linuser」として 153.120.41.188:22 への認証<br>
  
 kex: algorithm: curve25519-sha256<br>
 kex: host key algorithm: ecdsa-sha2-nistp256<br>
 kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none<br>
 圧縮なし<br>
 kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none<br>
 
 expecting SSH2_MSG_KEX_ECDH_REPLY<br>
 期待<br>
 SSH2_MSG_NEWKEYS received<br>
 受け取りました<br>
 
 Server host key: ecdsa-sha2-nistp256 SHA256:cvfmBW3/z643nV7ed+meqY1W4YhGgYr1xTrH1hjmzOA<br>
 Host '153.120.41.188' is known and matches the ECDSA host key.<br>
 ホスト '153.120.41.188' は既知であり、ECDSA ホスト キーと一致します。<br>
 
 Found key in C:\\Users\\coral/.ssh/known_hosts:2<br>
 
 rekey out after 134217728 blocks<br>
 134217728 ブロック後にキーを再生成する<br>
 
 SSH2_MSG_NEWKEYS sent<br>
 送った<br>
 expecting SSH2_MSG_NEWKEYS<br>
 期待する<br>
 SSH2_MSG_NEWKEYS received<br>
 受け取った<br>
 
 rekey in after 134217728 blocks<br>
 134217728 ブロック後に再キー入力<br>
 
 
 ##pubkey_prepare: ssh_get_authentication_socket: No such file or directory<br>
 ##pubkey_prepare: ssh_get_authentication_socket: そのようなファイルまたはディレクトリはありません<br>
 公開鍵の準備<br>
 
  Will attempt key: id_rsa RSA SHA256:n7eS/kbemIo6arCgtJB9AGzf6JOw5qEsCo61eq4O8f0 explicit<br>
 キーを試行します: id_rsa RSA SHA256: n7eS / kbemIo6arCgtJB9AGzf6JOw5qEsCo61eq4O8f0 明示的<br>
 
 SSH2_MSG_EXT_INFO received<br>
 
 kex_input_ext_info: server-sig-algs=<ssh-ed25519,sk-ssh-ed25519@openssh.com,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ecdsa-sha2-nistp256@openssh.com,webauthn-sk-ecdsa-sha2-nistp256@openssh.com><br>
 
  kex_input_ext_info: publickey-hostbound@openssh.com (unrecognised)<br>
 (認識されない)<br>
 
 SSH2_MSG_SERVICE_ACCEPT received<br>

Authentications that can continue: publickey<br>
継続できる認証: publickey<br>
Next authentication method: publickey<br>
 次の認証方法: publickey<br>

Offering public key: id_rsa RSA SHA256:n7eS/kbemIo6arCgtJB9AGzf6JOw5qEsCo61eq4O8f0 explicit<br>
公開鍵の提供: RSA id_rsa SHA256: n7eS / kbemIo6arCgtJB9AGzf6JOw5qEsCo61eq4O8f0 明示的<br>
*RSA:公開鍵の暗号方式<br>

 Authentications that can continue: publickey<br>
 継続できる認証: publickey<br>
 
  No more authentication methods to try.<br>
 もう認証方法を試す必要はありません。<br>
 
 linuser@153.120.41.188: Permission denied (publickey).<br>
 linuser@153.120.41.188: 許可が拒否されました (公開鍵)。<br>
 
