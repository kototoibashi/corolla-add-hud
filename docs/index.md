<div style="border:#008855 1px solid;border-radius:20px;padding:1em;">
詳細な情報は下記のリンクを読んでください。
<ol>
<li><a href="https://kuriuzublog.wordpress.com/2021/09/20/corolla-hud-1/">動作確認編</a></li>
<li><a href="https://kuriuzublog.wordpress.com/2021/09/24/corolla-hud-2/">配線編</a></li>
<li><a href="https://kuriuzublog.wordpress.com/2022/01/27/corolla-sport-hud-3/">取付編</a></li>
</ol>

</div>

**以下の文書は、下書きです。**

# はじめに
カローラスポーツHV (ZWE213H)のGグレードに純正HUDを後付けしたい！    
とりあえず中古でHUDモジュールだけ買ってきた。どうやって取り付ければいいか今調べている。  
取り付けが上手くいったら更新するかブログにまとめるかします。

* 純正HUDモジュール　型番: `83108-1E060`

# 接続

このHUDモジュールには16ピンのコネクタが一個ついている。  
コネクタ型番: [TE `1939082-9`](https://www.te.com/jpn-ja/product-1939082-9.html)

## ピン配列
![](https://media.githubusercontent.com/media/kototoibashi/corolla-add-hud/master/img/hud-connector-pinout.jpg)

| ピン番号 | 色 | ピン名 | 接続先 |  |
| -- | -- | -- | -- | -- |
| 1 | 紫`V` | IG | I102 Junction Connector | イグニッション電源 |
| 2 | スカイブルー`SB` | B | I98 No.8 Junction Connector | バッテリー電源 |
| 4 | 白・黒`W-B` | ES | I101 No.11 Junction Connector | アース |
| 12 | ライトグリーン`LG` | MPX1 | I94 No.3 CAN Junction Connector - pin3 | CAN通信(High) |
| 13 | 白`W` | MPX2 | I94 No.3 CAN Junction Connector - pin13 | CAN通信(Low) | 
| 14 | 黒`B` | TX+ | I108 No.2 Junction Connector - pin2 | ディスプレイオーディオ CNH1 |
| 14 | 黄`Y` | TX- | I108 No.2 Junction Connector - pin13 | ディスプレイオーディオ CNL1 | 



## 事前調査
実際の車のインパネをバラしてみたが、HUDに繋がりそうな空きコネクタは見つからなかった。ハーネスの自作が必要だろう。  

ディーラーに聞いてみたところ、HUDモジュールが付いている車には助手席側にコンピューターがついているが、Gグレードの実車を確認したところ付いていないということだった。HUDモジュールの動作に、このコンピューターが必須かどうかはわからない、とのこと。
（私の推理：MPXコンピューターが付いていないとか？）

# 解決すべき課題
* 配線はどうする？
  * ハーネスの購入・作成が必要なのか？
  * そもそもコンピューターがHUD対応しているのか？配線ポン付けでHUDを認識して動くのか？
* どうやって固定する？
  * ホームセンターで売っているステーで固定具を作れないか？

# 参考になりそうなページ
* [https://minkara.carview.co.jp/userid/2122549/car/2834247/5489693/note.aspx](https://minkara.carview.co.jp/userid/2122549/car/2834247/5489693/note.aspx)


# 補足
## 購入したHUDモジュール

* UPJ.parts　にて購入　
* 商品価格6820円+送料1200円
* 2UPJ-9175326239]カローラ スポーツ ハイブリッド(ZWE211H)メーター・その他 中古 

```
商品名    ： メーター・その他
部品メーカー名：
品番1     ： 83108-1E060
品番2     ： 257510-1545
商品情報   ： 作動確認：未テスト／【撮影画像以外にもキズ・破損・欠品などがある可能性があります。】
備考     ： 本商品は中古品になります。 充分な検品を心がけておりますが、隠れた箇所に不良があったり、見落としがある場合もございます。予めご了承下さい。

メーカー名   ： トヨタ
車名      ： カローラ スポーツ ハイブリッド
グレード    ： G Z
型式      ： 6AA-ZWE211H
型式指定番号  ： 18958
類別区分番号  ： 0002
フル型式    ： 6AA-ZWE211H-BHXNB−Z
エンジン型式  ： 2ZR-FXE
エンジン区分  ： 自然吸気
エンジンNo.   ： 2C38821
ミッション区分 ： MT
排気量     ： 1797 cc
燃料区分    ： ガソリン
駆動区分    ： 2駆
ハンドル区分  ： 右
パワステ区分  ： 電動
年式      ： 2018年11月
走行距離    ： 82012 km
カラーNo.    ： 3U4
トリムNo.    ： FB20
トランスNo.   ： P610
アクスルNo.   ： 01A
ミッションNo.等 ： 18L7W02436
ABSの有無   ： 有り
乗車定員    ： 5人
車台番号    ： ZWE211-1010***
車両備考    ： 
```
 
## カローラスポーツのCANバスの対応

### CAN1 / CANX
* ミリ波レーダー
* 前方認識カメラ
* ブラインドスポットモニターセンサ・左右
### CAN2
* ブレーキアクチュエータ
* 乗員検知
* エアバッグセンサ
* ステアリングセンサ
* パワーステアリング
### CAN3 / CANY
* ラジオ・カーナビ・ディスプレイオーディオ
* 電話トランシーバ (DCMのことか？)
### CAN4
* ECM(エンジンコントロール)
* トランスミッションコントロールECU
### CAN5
* コンビネーションメーター
* メーターミラー(HUD)
* エアコンアンプ
* ヘッドライトユニット・左右
* メインボディーECU
### CAN6
* DataLincConnector3 (OBD2)
