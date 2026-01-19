# QuantumIR Studio - インストールガイド

## 目次

1. [システム要件](#システム要件)
2. [ORCA のインストール](#orcaのインストール)
3. [QuantumIR Studio のインストール](#quantumir-studioのインストール)
4. [初回設定](#初回設定)
5. [動作確認](#動作確認)
6. [トラブルシューティング](#トラブルシューティング)

---

## システム要件

### 最小要件

| 項目 | 仕様 |
|------|------|
| OS | Windows 10 (64-bit) 以上 |
| CPU | Intel Core i5 / AMD Ryzen 5 以上（4コア） |
| メモリ | 8 GB RAM |
| ディスク | 20 GB 空き容量 |
| インターネット | ORCA ダウンロード時のみ必要 |

### 推奨要件

| 項目 | 仕様 |
|------|------|
| OS | Windows 11 (64-bit) |
| CPU | Intel Xeon / AMD Ryzen Threadripper (16コア以上) |
| メモリ | 32 GB RAM 以上 |
| ディスク | 50 GB 空き容量（SSD推奨） |

---

## ORCAのインストール

### ステップ1: アカウント登録

1. [ORCA公式サイト](https://orcaforum.kofo.mpg.de/)にアクセス
2. 右上の **"Register"** をクリック
3. メールアドレスと氏名を入力（学術利用は無料）
4. 登録完了メールが届く

### ステップ2: ORCAのダウンロード

1. ログイン後、**"Downloads"** タブに移動
2. **Windows版**を選択：
   ```
   Orca.6.1.1.Win64_msmpi.zip (5.8 GB)
   ```
   > ⚠️ **重要**: MS-MPI版を選択してください（OpenMPI版はWindows非対応）

3. ダウンロード（30-60分かかる場合があります）

### ステップ3: ORCAの展開

1. ダウンロードした `Orca.6.1.1.Win64_msmpi.zip` を右クリック
2. **"すべて展開..."** を選択
3. 展開先を選択（推奨: `C:\ORCA_6.1.1\`）
4. 展開完了まで待機（約10分）

### ステップ4: 確認

展開後、以下のファイルが存在するか確認：

```
C:\ORCA_6.1.1\
├── orca.exe             ← 量子化学計算本体
├── orca_mapspc.exe      ← スペクトル抽出ツール
├── orca_...exe          （その他多数のツール）
└── ...
```

---

## QuantumIR Studioのインストール

### ステップ1: ダウンロード

1. [QuantumIR Studio GitHub Releases](https://github.com/YOUR_USERNAME/QuantumIR-Studio/releases)にアクセス
2. 最新版の `QuantumIR_Studio_v2.exe` をダウンロード（約200-300 MB）

### ステップ2: セキュリティ警告の解除（必要な場合）

Windows Defenderが警告を出す場合：

1. ダウンロードした `QuantumIR_Studio_v2.exe` を右クリック
2. **"プロパティ"** を選択
3. 下部の **"ブロックの解除"** にチェック
4. **"OK"** をクリック

### ステップ3: 配置

任意の場所に配置（例: `C:\Users\YourName\Desktop\`）

---

## 初回設定

### ステップ1: QuantumIR Studio の起動

1. `QuantumIR_Studio_v2.0_Licensed.exe` をダブルクリック
2. 初回起動は少し時間がかかります（10-30秒）
3. **ライセンスキー入力ダイアログが表示されます**：

   ```
   ライセンスキー認証
   ライセンスキー: [入力欄]
   有効期限: 2028年03月31日
   ```

   **ライセンスキー**: `QuantumIRStudio2026` を入力して「認証」ボタンをクリック

4. 認証成功後、ORCA設定ダイアログが表示される場合があります：

   ```
   「ORCA設定が必要」
   ORCAの実行ファイルパスを「入力」タブで設定してください
   ```

   これは正常です。**"OK"** をクリック

### ステップ2: ORCAパスの設定

#### GUIでの設定

1. **"入力"** タブを開く
2. **"ORCA設定"** セクションで設定：

   **A. ORCA実行ファイル**
   - **"参照..."** ボタンをクリック
   - `C:\ORCA_6.1.1\orca.exe` を選択
   - **"開く"** をクリック

   **B. orca_mapspc**
   - **"参照..."** ボタンをクリック
   - `C:\ORCA_6.1.1\orca_mapspc.exe` を選択
   - **"開く"** をクリック

3. 設定は自動保存されます（`quantumir_config.ini`に保存）

### ステップ3: その他の設定

#### デフォルト計算設定

- **計算手法**: r2SCAN-3c（推奨）
- **並列コア数**: 使用可能なコア数に応じて調整
  - 例: 8コアCPU → 6-7コア設定
  - 例: 32コアCPU → 30コア設定
- **メモリ**: 2000 MB/core（標準）

---

## 動作確認

### テスト計算

1. **"入力"** タブで以下を入力：

   ```
   モノマーSMILES: CC(=C)C(=O)OC
   ポリマー名: MMA_test
   最小n: 1
   最大n: 1
   ```

2. **"計算開始"** ボタンをクリック

3. **"計算"** タブに自動切り替え

4. ログに以下が表示されれば成功：

   ```
   === ポリマーFTIR計算開始 ===
   モノマーSMILES: CC(=C)C(=O)OC
   化合物名: MMA_test
   ...
   [1量体] ステップ1/4: ポリマー構造生成中...
   ...
   ```

5. 計算完了（約2-5分）後、**"結果"** タブで spectrum を確認

---

## トラブルシューティング

### 問題1: exeファイルが起動しない

#### 症状
ダブルクリックしても何も起こらない

#### 解決策
1. Windows Defenderのブロック解除（上記参照）
2. 管理者権限で実行：
   - exeファイルを右クリック
   - **"管理者として実行"** を選択

### 問題2: 「ORCAのパスが正しくありません」エラー

#### 症状
計算開始時にエラーダイアログ

#### 解決策
1. ORCAが正しくインストールされているか確認
2. パスが正確か確認（スペースやタイポに注意）
   ```
   正: C:\ORCA_6.1.1\orca.exe
   誤: C:\ORCA_6.1.1\orca  （.exe が抜けている）
   ```

### 問題3: 計算が1コアしか使わない

#### 症状
タスクマネージャーでCPU使用率が低い（1コア分のみ）

#### 原因と解決策
1. **OpenMPI版を使用している**
   - Windows版は MS-MPI版が必要
   - ORCA を再ダウンロード（`Orca.6.1.1.Win64_msmpi.zip`）

2. **並列コア数が1に設定されている**
   - 入力タブで「並列コア数」を確認

### 問題4: メモリ不足エラー

#### 症状
```
ERROR: Not enough memory...
```

#### 解決策
1. **メモリ設定を増やす**
   - 入力タブ → メモリ: 2000 → 4000 MB/core

2. **または並列コア数を減らす**
   - 並列コア数: 30 → 15

3. **計算式**
   ```
   必要メモリ = メモリ/core × 並列コア数
   例: 2000 MB/core × 30 cores = 60 GB
   ```

### 問題5: RDKitエラー（Invalid SMILES）

#### 症状
```
Error: Invalid SMILES: ...
```

#### 解決策
SMILESの記法を確認：
- **正しい例**: `CC(=C)C(=O)OC`
- **誤り例**: `CC(C)C(O)OC` （メタクリル酸ではない）

参考: [RDKit SMILES Tutorial](https://www.rdkit.org/docs/GettingStartedInPython.html)

### 問題6: antivirus/firewall による誤検知

#### 症状
- exeファイルが自動削除される
- 「このファイルはウイルスです」警告

#### 解決策
1. **一時的にアンチウイルスを無効化**
   - Windows Defender → 設定 → リアルタイム保護をオフ
   - exeファイルを実行
   - リアルタイム保護を再度オン

2. **除外リストに追加**
   - Windows セキュリティ → ウイルスと脅威の防止
   - 設定 → 除外 → 除外の追加
   - `QuantumIR_Studio_v2.exe` を追加

---

## サポート

### 問い合わせ先

- **開発者**: Yuta Otsuka, Kagoshima University
- **GitHub Issues**: [https://github.com/YOUR_USERNAME/QuantumIR-Studio/issues](https://github.com/YOUR_USERNAME/QuantumIR-Studio/issues)

### よくある質問（FAQ）

詳細は [README.md](README.md) を参照してください。

---

**Developed by Yuta Otsuka, Kagoshima University**

**設定完了後、素晴らしいFTIR予測をお楽しみください！** 🎉

