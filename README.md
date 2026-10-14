# Mini Disperser

Allpass フィルターを最大128段直列にして位相を分散 (dispersion) させる、Kilohearts Disperser 風のエフェクトです。

| ノブ | 内容 |
|---|---|
| Amount | 0〜100%。通すオールパスの段数 (0〜128段、端数はクロスフェード) |
| Frequency | 20Hz〜20kHz。オールパスの中心周波数 (位相が180°回る点) |
| Pitch | -48〜+48 st。段ごとに周波数をずらす量。0なら全段同一周波数 |

## ビルド方法

### A. GitHub Actions (自分のPCに何もインストール不要)
1. GitHubで新しいリポジトリを作り、このフォルダの中身をpushする
2. リポジトリの Actions タブでビルド完了を待つ (5〜10分)
3. 完了した実行の Artifacts から Windows / macOS / Linux 用の VST3 等をダウンロード

### B. ローカル (CMake + コンパイラ)
```
cmake -B build
cmake --build build --config Release
```
- Windows: Visual Studio (C++デスクトップ開発) / macOS: Xcode Command Line Tools
- 初回は JUCE を自動取得します

### C. Projucer
JUCE付属のProjucerで新規Audio Pluginプロジェクトを作り、`Source/` の4ファイルを差し替える方法もあります。
