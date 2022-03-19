# python-blockchain

# サーバーの起動
blockchain_server.py: ブロックチェーンノード（-p: ポート指定(default=5000)）
wallet_server.py: ウォレットサーバー（-p: ポート指定（default=8080）, -g: ゲートウェイ指定(ブロックチェーンサーバーのアドレスを指定)（default: 5000））

# API
## /transactions
トランザクションの一覧（JSON形式）
## /chain
ブロックチェーンの一覧（JSON形式）
## /mine
マイニング（トランザクションキャッシュをブロックチェーンに入れ、トランザクションキャッシュを空にする）

# 使い方
1. blockchain_server.py を起動する
2. wallet_server.pyを起動し、タブを2つ開く（コインの送信側と受信側で2つ使う。）
3. blockchain_server.py起動時にログに出力されるpublic_key, private_key, blockchain_addressをwalletの送信側の画面に入力する
4. blockchain_serverでAPIの/mineを叩く（例：http://localhost:5000/mine）
5. 送信側のwalletの画面上方の数字が１になることを確認する（マイニングの報酬によってコインが１付与された状態）
6. 受信側の画面に出ているblockchain_addressを送信側の’Send Money’配下の’Address'に入れる。
7. 送信側の’Send Money’配下のAmountに1.0を入れ、Sendをクリック
8. ダイアログに確認が出てくるのでOK⇨Successが表示されれば送信が成功している。（まだブロックチェーンに追加されていない）
9. blockchain_serverでAPIの/mineを叩く（例：http://localhost:5000/mine）
10. 受信側の画面上部の数字が１になっていることを確認（送信側の数字が減っていないように見えるが、送信の後にマイニングの報酬で1が追加されているので１と表示されている。）
11. blockchain_serverでAPIの/transactions, /chainを叩くことでトランザクションからチェーンに追加されていく動きが確認することができる。


