# Changelog

All notable changes to QuantumIR Studio will be documented in this file.

## [2.0] - 2026-01-19

### Added
- ⚙️ **設定可能なORCAパス**: GUIで簡単にORCAの実行ファイルパスを設定可能
- 💾 **設定の自動保存**: `quantumir_config.ini`に設定を保存し、次回起動時に自動読み込み
- 📁 **ファイル選択ダイアログ**: 「参照...」ボタンでORCAファイルを簡単選択
- ⚠️ **初回起動ガイド**: ORCAが未設定の場合、警告ダイアログを表示
- 🔍 **自動検出機能**: `orca.exe`を選択すると、同じディレクトリの`orca_mapspc.exe`を自動検出

### Changed
- 🔧 ハードコードされたORCAパスを削除し、完全に設定可能に変更
- 📝 GUIに「ORCA設定」セクションを追加（入力タブ）
- 🎨 UI/UXを改善し、初心者でも設定しやすく

### Fixed
- ❌ **Critical**: ORCAパスのハードコーディング問題を解決
  - v1.0では特定のパスにORCAがインストールされている必要があった
  - v2.0では任意の場所のORCAを使用可能
- 🐛 Windows環境でのパス区切り文字の問題を修正

---

## [1.0] - 2026-01-18

### Added
- 🎉 **初回リリース**
- 🧬 SMILESからn量体（モノマー、ダイマー、トリマー等）を自動生成
- 🔬 ORCA 6.1.1による高精度FTIR予測（r2SCAN-3c, BP86等）
- ⚡ マルチコア並列計算対応（最大64コア）
- 📊 PCA解析機能
- 🖥️ PyQt5ベースのGUI
- 📈 FTIRスペクトルのリアルタイム可視化
- 📁 計算結果のCSVエクスポート
- 🎨 PNG/PDFでのグラフエクスポート

### Known Issues (v1.0)
- ⚠️ ORCAパスがハードコード（`C:\ORCA_6.1.1\`固定）
- ⚠️ 他の場所にORCAをインストールすると動作しない
- → **v2.0で解決済み**

---

## Coming Soon

### [2.1] - Planned
- 📊 PCA解析のGUI統合（現在はCLIのみ）
- 🎨 スペクトルプロット機能の拡張
  - 差スペクトル表示
  - ピークアノテーション
  - カスタムカラーマップ
- 💾 プロジェクトファイル機能（複数の計算をまとめて管理）
- 🌐 英語版UI

### [3.0] - Future
- 🤖 機械学習モデルの統合
  - スペクトルからの構造予測
  - 物性値予測
- 🧪 複雑なポリマー構造への対応
  - 共重合体
  - 架橋構造
  - ブレンド
- 🔗 他の量子化学ソフトとの連携
  - Gaussian
  - NWChem
  - GAMESS

---

## Version Naming

- **Major (X.0.0)**: 大きな機能追加や破壊的変更
- **Minor (x.Y.0)**: 新機能追加、重要なバグ修正
- **Patch (x.y.Z)**: 小さなバグ修正、ドキュメント更新

---

## Credits

**Developer**: Yuta Otsuka  
**Institution**: Kagoshima University  
**Year**: 2026

## Support

- GitHub Issues: https://github.com/YOUR_USERNAME/QuantumIR-Studio/issues
- Developer: Yuta Otsuka, Kagoshima University

