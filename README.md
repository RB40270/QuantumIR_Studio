# QuantumIR Studio - Polymer Edition 🧪

**ポリマー材料に特化した量子化学FTIR予測・PCA解析ツール**

![Version](https://img.shields.io/badge/version-2.0-blue.svg)
![Platform](https://img.shields.io/badge/platform-Windows-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

---

## ✨ 特徴

- 🔬 **量子化学計算**: ORCA 6.xによる高精度FTIR予測（r2SCAN-3c, BP86等）
- 🧬 **ポリマー特化**: モノマーSMILESから自動でn量体（ダイマー、トリマー等）を生成
- ⚡ **マルチコア対応**: 最大64コア並列計算で高速処理
- 📊 **PCA解析**: 機械学習による自動スペクトル分類
- 🖥️ **GUI操作**: 直感的なグラフィカルインターフェース
- ⚙️ **設定可能**: ORCAパスをGUIで簡単設定

---

## 📦 ダウンロード

### Windows版（64-bit）

**[QuantumIR_Studio_v2.0_Licensed.exe をダウンロード](dist/QuantumIR_Studio_v2.0_Licensed.exe)**

- **バージョン**: 2.0 (Licensed)
- **ファイルサイズ**: 約200-300 MB
- **対応OS**: Windows 10/11 (64-bit)
- **ライセンス**: 認証キー必須

### 📝 重要: ライセンスキーについて

初回起動時にライセンスキーの入力が必要です。

**ライセンスキー**: `QuantumIRStudio2026`
**有効期限**: 2028年3月31日まで

詳細は同梱の [LICENSE_KEY.txt](LICENSE_KEY.txt) を参照してください。

---

## 🚀 クイックスタート

### 必要なソフトウェア

#### 1. QuantumIR Studio（このツール）
上記からダウンロード

#### 2. ORCA 6.1.1（量子化学計算エンジン）
**[ORCA公式サイト](https://orcaforum.kofo.mpg.de/)からダウンロード**

- **Windows**: `Orca.6.1.1.Win64_msmpi.zip` (5.8 GB) - MS-MPI版推奨
- インストール先: 任意の場所（例: `C:\ORCA_6.1.1\`）

> ⚠️ **重要**: ORCAは別途ダウンロードが必要です（ライセンス上の理由）

---

## 📖 インストール手順

### ステップ1: ORCAのインストール

1. [ORCA公式サイト](https://orcaforum.kofo.mpg.de/)にアクセス
2. アカウント登録（無料）
3. `Orca.6.1.1.Win64_msmpi.zip`をダウンロード
4. 任意の場所に展開（例: `C:\ORCA_6.1.1\`）

### ステップ2: QuantumIR Studioの起動

1. `QuantumIR_Studio_v2.0_Licensed.exe`をダウンロード
2. ダブルクリックで起動
3. **初回起動時、ライセンスキー入力ダイアログが表示されます**
   - ライセンスキー: `QuantumIRStudio2026` を入力
   - 「認証」ボタンをクリック
4. 認証成功後、ソフトウェアが使用可能になります

### ステップ3: ORCAパスの設定

1. 「入力」タブを開く
2. 「ORCA設定」セクションで以下を設定：
   - **ORCA実行ファイル**: `C:\ORCA_6.1.1\orca.exe`を選択
   - **orca_mapspc**: `C:\ORCA_6.1.1\orca_mapspc.exe`を選択
3. 設定は自動保存され、次回起動時も有効

---

## 💡 使い方

### 基本ワークフロー

1. **モノマーSMILES入力**
   ```
   例: CC(=C)C(=O)OC  (MMA - メタクリル酸メチル)
   例: CC(=C)C(=O)OCCO  (HEMA - ヒドロキシエチルメタクリレート)
   ```

2. **ポリマー名設定**
   ```
   例: MMA, HEMA, PMMA, etc.
   ```

3. **鎖長範囲設定**
   - 最小n: 1（モノマー）
   - 最大n: 4（テトラマー）
   - → 4サンプルを自動生成

4. **計算設定**
   - 計算手法: r2SCAN-3c（推奨）
   - 並列コア数: 30（使用可能なコア数に応じて調整）
   - メモリ: 2000 MB/core

5. **計算開始**
   - 「計算開始」ボタンをクリック
   - 進捗とログをリアルタイム表示

6. **結果確認**
   - 計算完了後、自動的にFTIRスペクトルを表示
   - 結果タブで可視化
   - PNG/PDFでエクスポート可能

---

## 📁 出力ファイル

計算が完了すると、以下のファイルが生成されます：

```
output_directory/
├── structures/              # 3D分子構造（XYZ形式）
│   ├── compound_1mer.xyz
│   ├── compound_2mer.xyz
│   └── ...
├── orca_inputs/             # ORCA入力ファイル
│   ├── compound_1mer.inp
│   └── ...
├── orca_outputs/            # ORCA計算結果
│   ├── compound_1mer.out
│   ├── compound_1mer.hess
│   └── ...
└── results/                 # 抽出データ・スペクトル
    ├── all_spectra.csv          # 統合スペクトルデータ
    ├── metadata.csv             # サンプル情報
    ├── compound_1mer.ir.dat     # 個別IRスペクトル
    └── ...
```

### 重要なファイル

- **all_spectra.csv**: 全サンプルのIRスペクトル（PCA解析に使用可能）
- **metadata.csv**: サンプル名、化合物名、n量体情報
- ***.ir.dat**: 個別のIRスペクトルデータ（400-4000 cm⁻¹）

---

## ⏱️ 計算時間の目安

**システム**: AMD Ryzen Threadripper PRO 7975WX（30コア並列）  
**計算手法**: r2SCAN-3c OPT FREQ

| 構造 | 原子数 | 計算時間 |
|------|--------|----------|
| MMA モノマー | ~15 | 約2分 |
| MMA ダイマー | ~30 | 約5分 |
| MMA トリマー | ~45 | 約18分 |
| HEMA モノマー | ~20 | 約2分 |
| HEMA トリマー | ~60 | 約16分 |

> 💡 **ヒント**: コア数が少ない場合、比例して時間が増加します

---

## 🔧 トラブルシューティング

### Q1: ライセンスキーが認証できない

**エラー**: 「無効なライセンスキーです」

**解決策**:
- ライセンスキーを正確にコピー＆ペーストしてください: `QuantumIRStudio2026`
- 前後にスペースが入っていないか確認
- ライセンスキーファイル [LICENSE_KEY.txt](LICENSE_KEY.txt) を確認

**エラー**: 「ライセンスの有効期限が切れています」

**解決策**:
- 有効期限（2028年3月31日）を過ぎている場合、開発者にお問い合わせください
- Email: y.otsuka@dent.kagoshima-u.ac.jp

### Q2: 「ORCAのパスが正しくありません」エラー

**解決策**:
1. 「入力」タブの「ORCA設定」で正しいパスを設定
2. `orca.exe`が実際に存在するか確認
3. ファイル名が正しいか確認（`orca.exe`, `orca_mapspc.exe`）

### Q2: 計算が1コアしか使わない

**確認事項**:
- MS-MPI版のORCAを使用していますか？
  - OpenMPI版ではWindows上で並列化できません
- 並列コア数が正しく設定されていますか？
  - デフォルト: 30コア

### Q3: メモリ不足エラー

**解決策**:
- 「メモリ」設定を増やす（2000 → 4000 MB/core等）
- または並列コア数を減らす

### Q4: exeファイルが起動しない

**確認事項**:
- Windows Defenderでブロックされていませんか？
  - 右クリック → プロパティ → ブロック解除にチェック
- 管理者権限で実行してみてください

### Q5: RDKitエラー（Invalid SMILES）

**解決策**:
- SMILES記法が正しいか確認
- 例: `CC(=C)C(=O)OC` ← 括弧とイコールに注意
- [RDKit SMILES Tutorial](https://www.rdkit.org/docs/GettingStartedInPython.html)

---

## 📊 応用例

### 1. 異なるポリマーの比較
MMAとHEMAを別々に計算し、スペクトルを比較

### 2. 重合度の影響評価
1量体〜10量体を計算し、鎖長依存性を調査

### 3. 材料品質管理
実測スペクトルと理論スペクトルを比較

### 4. 新規モノマー設計
新しいSMILESでスペクトルを予測し、物性を事前評価

---

## ⚙️ システム要件

### 最小要件
- **OS**: Windows 10/11 (64-bit)
- **CPU**: 4コア以上
- **メモリ**: 8 GB以上
- **ディスク**: 10 GB以上の空き容量

### 推奨要件
- **OS**: Windows 11 (64-bit)
- **CPU**: 16コア以上（Ryzen/Threadripper, Xeon等）
- **メモリ**: 32 GB以上
- **ディスク**: 50 GB以上の空き容量（SSD推奨）

---

## 🛠️ 技術詳細

### 使用ソフトウェア・ライブラリ

| ソフトウェア | バージョン | 用途 |
|-------------|-----------|------|
| **ORCA** | 6.1.1 | 量子化学計算（DFT, 振動数） |
| **RDKit** | 2023.9+ | SMILES → 3D構造変換 |
| **PyQt5** | 5.15+ | GUIフレームワーク |
| **NumPy** | 1.21+ | 数値計算 |
| **Pandas** | 1.3+ | データ処理 |
| **scikit-learn** | 1.0+ | PCA解析 |
| **Matplotlib** | 3.4+ | スペクトル可視化 |

### 計算手法

- **DFT法**: r2SCAN-3c（複合DFT法、推奨）
  - 精度とスピードのバランスが良い
  - 分散力補正含む
- **構造最適化**: UFF力場（RDKit） → DFT最適化（ORCA）
- **振動数計算**: 解析的Hessian
- **ブロードニング**: ローレンツ関数（半値半幅: 50 cm⁻¹）

---

## 📜 ライセンス

**Academic Use License**

```
Copyright (c) 2026 Yuta Otsuka, Kagoshima University

本ソフトウェアは学術・研究目的のみに使用できます。
商用利用は禁止されています。
```

### 引用

本ツールを使用した研究を発表する場合、以下を引用してください：

```bibtex
@software{quantumir_studio_2026,
  title={QuantumIR Studio: Polymer-Specialized FTIR Prediction Software},
  author={Otsuka, Yuta},
  institution={Kagoshima University},
  year={2026},
  version={2.0},
  url={https://github.com/YOUR_USERNAME/QuantumIR-Studio}
}
```

### ORCAの引用

```bibtex
@article{neese2022orca,
  title={Software update: The ORCA program system--Version 5.0},
  author={Neese, Frank},
  journal={Wiley Interdisciplinary Reviews: Computational Molecular Science},
  volume={12},
  number={5},
  pages={e1606},
  year={2022},
  publisher={Wiley Online Library}
}
```

---

## 🤝 サポート

### 問い合わせ先
- **開発者**: Yuta Otsuka
- **所属**: Kagoshima University
- **GitHub Issues**: [GitHub Repository](https://github.com/YOUR_USERNAME/QuantumIR-Studio/issues)

### よくある質問
- [FAQ Wiki](https://github.com/YOUR_USERNAME/QuantumIR-Studio/wiki/FAQ)

---

## 🙏 謝辞

このソフトウェアは以下のオープンソースプロジェクトを使用しています：

- **ORCA** - Frank Neese and ORCA Team
- **RDKit** - RDKit Community
- **PyQt5** - Riverbank Computing
- **NumPy, Pandas, scikit-learn** - Scientific Python Community

---

## 📝 更新履歴

### v2.0 (2026-01-19)
- ✨ ORCAパスをGUIで設定可能に
- ✨ 設定ファイル（`quantumir_config.ini`）による自動保存
- ✨ 初回起動時の設定ガイド追加
- 🐛 パスのハードコーディング問題を修正

### v1.0 (2026-01-18)
- 🎉 初回リリース
- ✅ 基本機能実装

---

---

**Developed by Yuta Otsuka, Kagoshima University**

**Made with ❤️ for Polymer Science**

---

## サンプルデータ

`examples/`フォルダに以下のサンプルデータを含みます：

- MMA（モノマー〜トリマー）のFTIRスペクトル
- HEMA（モノマー〜トリマー）のFTIRスペクトル
- PCA解析結果

これらのデータを使って、ツールの機能を確認できます。

