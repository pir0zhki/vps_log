# 文字化けについてのまとめ
Apache導入時に発生

## 原因
GUIのために言語関連の環境変数を日本語設定にしていたため<br>
<br>
UbuntuのGUIでは**LANG=ja_JP.UTF-8**で日本語表記okだが，<br>実機コンソールでは文字化けの原因になってしまうらしい<br>
(GUIのコンソールではLANG=ja_JP.UTF-8のままで正常に表示される)<br>

## 解決までの道のり

```
sudo LANG=C apt update
```
で英語表記に変更<br>
しかし，まだ文字化けしていた。。。
```
locale
```
で言語関連の環境変数の一覧を表示<br>
<br>
結果<br>

<img src="./PrtSc/LANG.png">

LANGUAGEだけjap_JP:jaになっていた...

```
LANGUAGE=C
```
で文字化け解消☆

## 参考
https://eng-entrance.com/linux-localization-lang
