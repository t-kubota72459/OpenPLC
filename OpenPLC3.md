# ラズパイ PLC で Pick & Place を動かす

*ラズベリーパイからリレーを駆動し AC 100V を ON/OFF するために　DC２４アイソレート I/O 基板を作る。*

ラズパイの GPIO 端子は 3.3V 数 mA しか出力できない。このままでは、 AC100V を ON/OFF するためのリレーの駆動はできない。そこでラズパイに外付けの DC24V アイソレート I/O 基板を作成する。

まず I/O 基板の回路の動きを開設しその後ユニバーサル基板上での部品の配置方法や制作のコツについて触れる。

## Pick & Place に必要な I/O

マイコン(PLC) 側から見た入力：

マイコン (PLC) 側から見た出力：

## なぜ DC24V?

### メーカー製 PLC の I/O には DC24V が使われている

多くの PLC では DC24 V がI/O に使われている。DC24V という電圧は電子回路やマイコンではあまり使われることはない。

マイコンは 3.3V や 5V の世界。PLC は 24V の世界。

<center>
<img src="./images/3-24.png" width="50%">
</center>

どのようにマイコンと PLC の間で信号をやりとりするか？これが PLC マイコン化計画の問題になる。

<center>
<img src="./images/FX5U.png" width="60%">
</center>

## ステップ１フォトカプラ

このような問題を取り扱うにはセンサー工学で学んだ「フォトカプラ」を用いる。
フォトカプラ…覚えていますか？

フォトカプラを使うことにより 5V の信号を光に変え、24V の信号を光に変え、相手に渡してあげることで、動作電圧の違いを吸収する。

<center>
<img src="./images/photokapura.png" width="50%">
</center>

<a href="https://drive.google.com/file/d/1PmLE28Ua4LTSeXLcicvdSTNaa-WGs759/view?usp=drive_link">センサ工学5.pdf</a>


## ステップ２トランジスタ

トランジスタを用いて 5V から光になった信号を 24V に増幅する。
