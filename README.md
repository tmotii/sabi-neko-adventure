# サビ猫アドベンチャー

夕方のまちを歩く地域猫のサビを操作して、ネズミをよけ、みぞを飛びこえ、カリカリを集めてゴハンまで進むドット絵アクションゲームです。

- 操作: ← → で移動、スペースでジャンプ(スマホは画面のボタン)
- 画像・音楽・効果音はすべてコードで生成したオリジナルです。外部の画像や音源は使っていません。
- 依存ライブラリなし。ビルド不要。`index.html` だけで動きます(文字は Google Fonts の DotGothic16、読み込めない場合は端末の日本語フォントで表示)。

## ファイル

| ファイル | 役割 |
|---|---|
| `index.html` | ゲーム本体(HTML・CSS・JavaScript) |
| `manifest.webmanifest` | ホーム画面に追加したときの名前・アイコン・向きの設定 |
| `sw.js` | オフラインで遊べるようにするキャッシュ処理 |
| `icons/` | アプリのアイコン |

## ローカルで動かす

```sh
python3 -m http.server 8000
# ブラウザで http://localhost:8000 を開く
```

`index.html` をダブルクリックして開いても遊べますが、オフライン対応(Service Worker)は `http://localhost` か `https://` のときだけ有効になります。

## GitHub Pages で公開する

1. GitHub で新しいリポジトリを作る(例: `sabi-neko-adventure`)。
2. このフォルダで次を実行する。

   ```sh
   git remote add origin https://github.com/<ユーザー名>/sabi-neko-adventure.git
   git push -u origin main
   ```

3. リポジトリの Settings → Pages で、Source を「Deploy from a branch」、Branch を `main` / `/ (root)` にして保存する。
4. 数分後に `https://<ユーザー名>.github.io/sabi-neko-adventure/` で遊べる。

## スマホのホーム画面に追加する

- iPhone(Safari): 共有ボタン → 「ホーム画面に追加」
- Android(Chrome): メニュー → 「ホーム画面に追加」または「アプリをインストール」

## 更新するとき

`index.html` などを変えたら、`sw.js` の `VERSION`(`sabi-v1` など)を書き換えてください。遊んでいる人の端末に残った古いキャッシュが入れ替わります。
