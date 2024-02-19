# OpenPLC Editor

## 入出力の設定

以下のように変数 (入出力) を設定する。

|#|名前|Class|種類|Location|Initial Value|Option|Documentation|
|-|---|------|---|---------|-----------|-------|--------|
|1|SW1|Local|BOOL|%IX0.3|空き|空き|SET スイッチ |
|2|SW2|Local|BOOL|%IX0.4|空き|空き|RESET スイッチ |
|3|CR1|Local|BOOL|%QX2.0|空き|空き|セット |
|4|CR2|Local|BOOL|%QX2.1|空き|空き|リセット |
|5|CR3|Local|BOOL|%QX0.0|空き|空き|保持 |

## ラダープログラムの作成

# デバッグ機能

OpenPLC エディタには 2 つのデバッグ機能がある。

- プログラムのモニタ機能
- 変数モニタ機能
