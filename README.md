# 英語ドリル

日本語を見て英語を入力する、記述式の学習アプリです。単語も英文も登録できます。
ブラウザだけで動くため、Windows でも Android でも同じファイルで使えます。

## 主な機能
- 出題数を設定でき、全問終了後に総合点を表示
- 間違えた問題は、全問正解するまで繰り返し出題
- 正解の読み上げ、音声入力での解答(対応ブラウザのみ)
- 発音記号の表示(アメリカ / イギリスの切り替え)
- グループ(日付など)ごとの出題範囲の選択

## ファイル構成
| ファイル | 内容 |
|---|---|
| `english-drill.html` | アプリ本体 |
| `cmudict-ipa.json` | アメリカ発音の辞書(CMUdict から生成) |
| `britfone-ipa.json` | イギリス発音の辞書(Britfone から生成) |
| `dictionary/` | 辞書のライセンス(削除しないでください) |

## 使い方
1. `https://ユーザー名.github.io/リポジトリ名/english-drill.html` を開きます。
2. 「CSVを読み込む」で問題データを登録します(読み込むと自動で保存されます)。

### CSV の書き方
```
犬,dog
酸っぱい！,It's tart! / It's sour!,#2026-11-21
元気です,"Good, thank you.",[ɡʊd θæŋk juː]
```
列は `日本語,英語,[発音記号],#グループ名` です。
- 発音記号とグループ名は省略できます。
- 正解が複数ある場合は、英語を ` / `(前後に空白)で区切ります。
- 英語にカンマを含む場合は、`"Good, thank you."` のように `"` で囲みます。
- CSV を読み込むと、日本語が同じ行は更新、新しい行は追加されます。文字コードは UTF-8 / Shift_JIS を自動判別します。

### 発音記号
- データに発音記号がない問題は、答え合わせのときに辞書を引いて表示します(データは変わりません)。
- データに発音記号を書いた問題は、それを優先して表示します。
- イギリス発音は、辞書にない語をアメリカ発音で補い、`*` を付けます。
- どちらの辞書にもない語は `?` と表示します。
- 単語ごとの発音を示すもので、文中の弱まりやつながりは反映しません。

### 読み上げ・音声入力
- 「発音」の選択に合わせて、アメリカ英語(en-US)かイギリス英語(en-GB)になります。
- 実際に使える声は、端末やブラウザにある音声によります。イギリス英語の音声がない端末では、別の声になる場合があります。
- 音声入力は、対応ブラウザ(Chrome、Edge など)のみで使えます。ネット接続が必要な場合があります。

### データの保存場所
問題データと設定は、ブラウザの localStorage に保存されます(端末・ブラウザ・URL ごとに別々です)。サイトデータを消すとデータも消えるため、元の CSV は手元に残してください。

## GitHub にアップロードするファイル
| ファイル | 必要性 |
|---|---|
| `english-drill.html` | 必須 |
| `cmudict-ipa.json`, `britfone-ipa.json` | 必須(発音記号の表示に使用) |
| `dictionary/LICENSE-cmudict.txt`, `dictionary/LICENSE-britfone.txt` | 必須(辞書のライセンスで、再配布時に添えるよう求められています) |
| `README.md` | 推奨(出典の記載) |

自分の問題データの CSV は、公開リポジトリに置かないでください。

## 出典・ライセンス
発音記号の表示には、次の辞書のデータを使用しています。

**The CMU Pronouncing Dictionary** (アメリカ発音)
Copyright (C) 1993-2015 Carnegie Mellon University. All rights reserved.
https://github.com/cmusphinx/cmudict
ライセンス:`dictionary/LICENSE-cmudict.txt`

**Britfone** (イギリス発音)
Copyright (c) 2017 Jose Llarena. MIT License.
https://github.com/JoseLlarena/Britfone
ライセンス:`dictionary/LICENSE-britfone.txt`

`cmudict-ipa.json` と `britfone-ipa.json` は、上記の辞書から生成した派生データです。再配布する場合は、著作権表示、ライセンスの条件、免責事項を残してください。
