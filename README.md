# クートラ翻訳機

くーちゃん・虎ちゃんの鳴き声を録音して、音の高さ・長さ・リズムから
「気持ちの傾向」を推定する、遊びの翻訳アプリ（クライアントのみ・データは端末内保存）。

## これは何をしているか（正直な説明）
- マイク/音声ファイルから音響特徴を抽出（ピッチ=自己相関法、音量エンベロープ、ゼロ交差率など）
- ルールベースで「ゴロゴロ/シャー/挨拶/要求…」等に分類
- 「判定が違う」で手動補正すると、その端末の個体データとして学習（nearest neighbor）
- ※本物の翻訳ではなく傾向の推定。猫語翻訳は科学的に未確立なので「当たる占い」程度

## 重要：動かすにはURL（https）で開くこと
マイク録音（getUserMedia）は **https:// か localhost でしか動きません**。
ダウンロードしたHTMLをダブルクリック（file://）で開くと、録音がブロックされます。
→ GitHub Pages 等に公開して、SafariでそのURLを開くこと。

## 公開（GitHub Pages）
- リポジトリ: https://github.com/kojiiphone1-cloud/kutora-honyaku
- 公開URL: https://kojiiphone1-cloud.github.io/kutora-honyaku/
- `index.html` をpushするとGitHub Pagesが自動で再公開

## iPhoneのホーム画面にアプリとして追加する
1. **Safari**（Chromeやアプリ内ブラウザ不可）で公開URLを開く
2. 下の共有ボタン（□に↑）→「ホーム画面に追加」
3. 追加すると全画面のアプリとして起動し、マイクも使える

## ローカルで試す
```
cd このフォルダ
python3 -m http.server 8778
# → http://localhost:8778 をブラウザで開く（localhostなのでマイクも動く）
```

## ファイル
- `index.html` — アプリ本体（1ファイル完結）
- `apple-touch-icon.png` / `icon-192.png` / `icon-512.png` — ホーム画面アイコン
- `manifest.json` — PWA設定
