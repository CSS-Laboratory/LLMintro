# LLMintro

> **大規模言語モデルの中身を覗いてみる ― Qwen3-8B で学ぶ "感情ベクトル" 入門**
>
> An introductory hands-on lecture notebook about Large Language Models for media studies undergraduates, using Qwen3-8B to extract and validate emotion vectors.

メディア研究を専攻する学部生のための、**LLM の内部表現を実際に取り出して観察する** ハンズオン講義ノートブックです。Google Colab の無料 T4 GPU 上で完結します。

By: [Kunhao Yang](https://khyang-lab.org/) — CSS Laboratory, Shibaura Institute of Technology
---

## 学生用 (Students): 講義ノートブックを開く

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/CSS-Laboratory/LLMintro/blob/main/lecture_notebook.ipynb)

上のバッジをクリックすると、Google Colab で直接ノートブックが開きます。

**実行環境の設定:**
1. Colab メニュー → 「ランタイム」→「ランタイムのタイプを変更」→「T4 GPU」を選択
2. 上のセルから順に実行 (再生ボタン ▶ をクリック)
3. 全部読み終わるまで約 60-90 分

**所要 VRAM:** 約 6 GB (Qwen3-8B 4-bit 量子化)

---

## 講義の構成

1. **準備運動: LLM に届く前の私たちの言葉** ― チャットテンプレートと「思考モード」
2. **ニューラルネットワーク入門** ― なぜ層を重ねると賢くなるのか (PyTorch MLP デモ)
3. **Forward Hook: モデルの中を覗く窓** ― 隠れ状態を取り出す技術
4. **感情ベクトルを抽出する** ― 280 個のストーリーから "怒り方向" を計算
5. **感情ベクトルは何を表現しているのか?** ― 幾何学とラベル付き実テキストでの検証

すべての解説は **日本語** で書かれており、コードセルは **デフォルトで折りたたまれて** います。コードに興味がない学生は文章と図だけを追って学べます。

---

## 講師用 (Instructors): キャッシュデータの再生成

学生ノートブックは `data/` フォルダ内のキャッシュデータを使います。同じ講義を再利用する場合はこのまま使えますが、新しい感情リストや異なる規模で再生成したい場合は、以下のノートブックを実行してください。

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/CSS-Laboratory/LLMintro/blob/main/prepare_cache.ipynb)

`prepare_cache.ipynb` を Colab T4 で実行すると、以下のファイルが `/content/cache_to_upload/` に生成されます:

| ファイル | サイズ | 内容 |
|---|---|---|
| `stories_smoke.jsonl` | 約 300 KB | 14 感情 × 20 ストーリー |
| `activations_smoke.npz` | 約 2 MB | 280 ストーリーの隠れ状態 (層 24, fp16) |
| `emotion_vectors_smoke.npz` | 約 100 KB | 14 個の最終感情ベクトル |

これらを `data/` フォルダに上書きアップロードしてください。

---

## リポジトリ構成

```
LLMintro/
├── README.md                       ← このファイル
├── lecture_notebook.ipynb          ← 学生用 (講義の本体)
├── prepare_cache.ipynb             ← 講師用 (キャッシュ再生成)
└── data/
    ├── stories_smoke.jsonl
    ├── activations_smoke.npz
    └── emotion_vectors_smoke.npz
```

---

## 参考文献 / References

- Anthropic (2026). [*Emotion Concepts and Their Function in a Large Language Model*](https://www.anthropic.com/research/emotion-concepts-function).
- Burns et al. (2023). *Discovering Latent Knowledge in Language Models Without Supervision.* ICLR.
- Russell, J. A. (1980). *A circumplex model of affect.* JPSP.
- Saravia et al. (2018). *CARER: Contextualized Affect Representations for Emotion Recognition.* EMNLP. (`dair-ai/emotion`)
- Qwen Team (2025). [Qwen3-8B Model Card](https://huggingface.co/Qwen/Qwen3-8B).

---

## ライセンス / License

教育目的で自由に使用・改変できます。改変版を公開する場合は、出典としてこのリポジトリへのリンクを明記してください。

The notebooks are provided for educational use. If you redistribute or adapt them, please credit this repository as the source.

---

## 連絡先 / Contact

楊鯤昊 (Kunhao Yang)  
Assistant Professor, Shibaura Institute of Technology  
GitHub Issues での質問・改善提案を歓迎します。
