##　Pyparrotでドローン実習

Pyparrotを使って、ドローンのMamboを動かします。こちらで環境構築、サンプルコードを編集した

インストール
MamboはPyparrotというライブラリを使って操作します。
まずはPyparrotのインストールをやってみましょう！
まずはMacを使っている人はTerminal、Windowsを使っている人はコマンドプロンプトを開いてください。下に書いてあるコードを一行ずつ実行してみてください。
```
conda create -n drone python=3.6 anaconda
conda activate drone
conda install -y -c anaconda opencv
conda install -y -c menpo
brew install ffmpeg
pip install untangle
pip install zeroconf
pip install pyparrot
```

Wifiをチェックする
インストールが終了したら、MamboをUSBに接続してください。PCでWifi接続一覧を確認してMambo_******といった形で表示されていれば成功です。
MACアドレス
お持ちのMambo特有のMACアドレスを調べておく必要があります。調べ方は[MACアドレスの調べ方](https://memorva.jp/internet/pc/network_mac_address.php)を参考にしてください。

```
安水さんドローンMAC：f0:18:98:71:e7:08
平岡のドローンMAC: e0:14:d0:63:3d:d0

安水のドローンWifi：Mambo_751161
平岡のドローンWifi：Mambo_785685
```

```
ffplay rtsp://192.168.99.1/media/stream2
```
でカメラを起動することができます。

プログラミング言語Pythonを使ったドローンのコントロールを体験してもらいます。

tutorial.pyファイルを開きます。
```
if (mambo.sensors.flying_state != "emergency"):
~~~
mambo.safe_land(5)
```
の間で、下に書かれているコードを自由に記述していきます。

静止
```
mambo.smart_sleep()
```
何もせずに空中(地上)に静止します。()のなかに入れた数字の時間静止します。

移動
```
mambo.fly_direct(roll=0, pitch=0, yaw=50, vertical_movement=0, duration=1)
```
roll: 正だと右へ。負だと左へ。
pitch: 正だと前へ。負だと後へ。
yaw: 正だと右に旋回。負だと左に旋回。
vertical_movement: 正で上に上昇。負で下降。
duration: 実行時間
duration以外の値は-100~100のなかで設定します。

方向転換
```
mambo.turn_degrees(90)
```
()のなかに-180~180の値を入力します。
例えば、90を入れると右に90°方向転換します。


宙返り
```
mambo.flip(direction="front")
mambo.flip(direction="back")
mambo.flip(direction="right")
mambo.flip(direction="left")
```
このコマンドでドローンを宙返りさせることができます。
direction以下で前転、後転などを指定することができます。


mambo.disconnect()
