# 表示・非表示
## 手段1 jQureyを使用した場合
### jqueryが一時的にできたり，できなかったりする
(できない時が多い)
### 対象のコード
クリックするとclass=hiddenが追加されたり，消去されたりする(動作確認済み)
```
$(ducument).ready(function(){
  $('.container').on('click',function(){
      $('.container p').toggleClass('hidden');
  });
});

```
### 確認したこと
- jqueryのscriptのパスは正しい
- 該当のscript.jsよりも上に記載
- インターネットには接続されている
- コンソールにエラーはなし
### やってみたこと
- jqueryのvertionを最新のものに変更→変化なし
- 
```
 $(document).ready(function(){
    ...
});
```
を
```
$(window).on('load',function(){
    ...
});
```
や
```
window.onload=function(){
    ...
};
```
に変更してみる→変化なし
- $(document).ready...の部分を削除→変化なし

## 手段2 jQueryを使わずに書く
visibilityを使用
```
function clickPic(){
  const co=document.getElementById('comment');
  if(co.style.visibility=='visible'){
    co.style.visibility='hidden';
  }else{
    co.style.visibility='visible';
  }
};
window.onload=function(){
  document.getElementById('comment').style.visibility='hidden';//error
  const pic=document.getElementsById('container');
  pic.addEventListener('click',clickPic);
};
```
- #commentに対してdocument.getElementById(...) is nullのエラー
- 読み込み順の影響か

### 試したこと
以下のように書き換え
- 全てのタグを読み込み終わった後に実行
```
 $(document).ready(function(){
    ...
});
```
- 画像を含めた全ての要素を読み込み終わった後に実行
```
$(window).on('load',function(){
    ...
});
```
- scriptを２つに分割し，より下位の方に該当のコードを移植
- fetchの中でformatJSONの後に.then()を追加
→addEventListener is not a functionが発生<br>
#### addEventListener is not a functionの原因
参考:https://bobbyhadz.com/blog/javascript-addeventlistener-is-not-a-function
- addEventListenerが有効ではない範囲で使用されているために発生?
- window.addEventListener()の中のfetchの中に配置しても使えない
