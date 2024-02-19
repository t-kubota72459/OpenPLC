# OpenPLC 起動

Windows (RaspberryPi でブラウザを立ち上げてもいいが遅い！) でブラウザを立ち上げ、http://<名前>-pi:8080/ にアクセスする。


username: openplc  
password: openplc 

でログインする。

**http と https の違いは前回話した通り。注意しましょう。**

<center>
<img src="./images/2024-02-19 (2).png" width="50%">
</center>

## 最初に必要な設定

まず最初にダッシュボードの左のメニューから Hardware をクリックし、RaspberryPi を選択して、下の方の "Save changes" をクリックする。
そうすると必要な準備が完了する。

この設定は１回だけ行えばよい。

<center>
<img src="./images/2024-02-19 (3).png" width="50%">
</center>

## ラダープログラムの実行

OpenPLC Editor で作ったラダープログラム（ラダーでなくてもいいけど）を Raspberry Pi に転送して OpenPLC Runtime 上で動作させる。
ここでは、前回作成した 1 bit の状態保持回路を転送してみる。

### 手順

#### ラダープログラムをコンパイルして転送用のファイルを作る

↓ボタンをクリックするとラズパイ用の実行ファイルが生成（コンパイル）される。拡張子は 〇〇〇.st になる。
<center>
<img src="./images/compile.png" width="50%">
</center>

ダッシュボードの Programs メニューからファイルを選択し、いま生成した〇〇〇.st をラズベリーパイにアップロードする。

<center>
<img src="./images/upload.png" width="70%">
</center>

Name (名前)、Description (説明) を加えて Upload Program ボタンをクリック。

<center>
<img src="./images/programinfo.png" width="70%">
</center>

### プログラムを起動する

左側の Start PLC ボタンをクリックする。

<center>
<img src="./images/start_bt.png">
</center>

## 動作プログラムのモニタリング

Dashboard の Monitoring メニューを選ぶと、現在動作しているプログラムの変数が現れる。

<center>
<img src="./images/monitor2.png" width="70%">
</center>

# 確認用回路を作ってみよう

せっかくなので確認用の回路を作ってみよう。ブレッドボード上にタクト SW x 2、LED を用意して接続してラズパイと接続してみよう。

<center>
<img src="./images/test1.png" width="50%">
<img src="./images/photo.png" width="50%">
</center>

## SW1/SW2 ボタンを押してみる

SW1 を押すと LED が点灯する。離しても点灯したまま（記憶される）。
SW2 を押すと LED が消灯する。（リセット）

またウェブブラウザ画面でも SW1, SW2, CR1, CR2, CR3 の状態がリアルタイムに更新される。(ただし 100ms 更新なのでタイムラグを感じる)

- SW1 を押したとき。SW1, CR1, CR3 が ON
<center>
<img src="./images/active1.png" width="50%">
</center>

- SW2 を押したとき。SW2, CR2 が ON, CR3 は FF
<center>
<img src="./images/active2.png" width="50%">
</center>

# プログラムの終了

画面左のボタン「Stop PLC」をクリックすると PLC のプログラムが終了する。

