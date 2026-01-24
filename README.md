# ReuleauxPhysics
ルーローの三角形で物理演算

<img width="914" height="909" alt="image" src="https://github.com/user-attachments/assets/7ef68d32-7643-4d49-b04c-8cb86da7988a" />


# ルーローの三角形とは

どの方向から測っても幅が一定である三角形です。

<img width="721" height="408" alt="image" src="https://github.com/user-attachments/assets/19b3425e-cb4a-4706-8fbc-8cacffa767ea" />


# 技術仕様

## 使用技術

- HTML5 Canvas
- Vanilla JavaScript (ES6+)
- CSS3

## ファイル構成

```
ReuleauxPhysics/
├── index.html    # メインHTML
├── main.js       # 物理演算・描画ロジック
├── styles.css    # スタイルシート
├── favicon.svg   # ファビコン
└── README.md     # このファイル
```

## 物理演算の仕組み

### 衝突検出

- **ルーローの三角形同士**: 境界点の最近接点を計算し、貫通深度と衝突法線を求める
- **壁との衝突**: 境界点が壁を貫通しているかチェックし、最も深い貫通点で衝突処理

### 衝突応答

- **インパルスベースの物理演算**: 法線方向と接線方向のインパルスを計算
- **反発係数**: 0.3〜0.4（弾性衝突の度合い）
- **摩擦係数**: 0.3（クーロン摩擦モデル）
- **回転の考慮**: 慣性モーメントを用いて角速度も更新

### 主要クラス・関数

| 名前 | 説明 |
|------|------|
| `ReuleauxGeometry` | ルーローの三角形のジオメトリ計算ユーティリティ |
| `ReuleauxTriangle` | 三角形オブジェクトのクラス（位置、速度、物理パラメータを管理） |
| `checkReuleauxCollision()` | 2つの三角形の衝突を検出 |
| `resolveCollision()` | 衝突を解決し、速度と位置を更新 |
| `animate()` | アニメーションループ |

## 物理パラメータ

| パラメータ | 値 | 説明 |
|-----------|-----|------|
| 質量 | `size² × 0.01` | サイズに比例 |
| 慣性モーメント | `0.5 × mass × size²` | 円盤として近似 |
| 最大速度 | 25 | 速度の上限 |
| 最大角速度 | 0.5 | 角速度の上限 |
| 空気抵抗 | 0.998（並進）, 0.995（回転） | フレームごとの減衰 |

