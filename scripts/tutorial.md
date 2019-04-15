今日はプログラミング言語Pythonを使ったドローンのコントロールを体験してもらいます。


tutorial.pyファイルを開きます。

if (mambo.sensors.flying_state != "emergency"):
から
mambo.safe_land(5)
の間で、下に書かれているコードを自由に記述していきます。

静止
mambo.smart_sleep()
何もせずに空中(地上)に静止します。()のなかに入れた数字の時間静止します。

移動
mambo.fly_direct(roll=0, pitch=0, yaw=50, vertical_movement=0, duration=1)
roll: 正だと右へ。負だと左へ。
pitch: 正だと前へ。負だと後へ。
yaw: 正だと右に旋回。負だと左に旋回。
vertical_movement: 正で上に上昇。負で下降。
duration: 実行時間
duration以外の値は-100~100のなかで設定します。

方向転換
mambo.turn_degrees(90)
()のなかに-180~180の値を入力します。
例えば、90を入れると右に90°方向転換します。


宙返り
mambo.flip(direction="front")
mambo.flip(direction="back")
mambo.flip(direction="right")
mambo.flip(direction="left")
このコマンドでドローンを宙返りさせることができます。
direction以下で前転、後転などを指定することができます。


mambo.disconnect()
