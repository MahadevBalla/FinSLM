# FinSLM

FinSLM is a small GPT-style language model trained from scratch on financial news text.

The model has approximately 30M parameters and uses a 6-layer, 6-head decoder-only Transformer with a 384-dimensional embedding size and 128-token context length. The implementation is based on a lightly modified version of [nanoGPT](https://github.com/karpathy/nanoGPT).

## Dataset

The training corpus combines three publicly available financial news datasets:

- Bloomberg Financial News
- Financial News Articles
- Indian Financial News

After preprocessing, the dataset contains approximately 480M training tokens.

## Experiments

Two training configurations were compared:

|                       |     Run 1 |  Run 2 |
| --------------------- | --------: | -----: |
| Learning rate         |      3e-4 |   1e-4 |
| Gradient accumulation |         4 |     32 |
| Max iterations        |    20,000 | 60,000 |
| Best validation loss  | **3.508** |  3.997 |
| Best perplexity       |  **33.4** |   54.5 |

Run 1 achieved lower validation loss and perplexity while using a shorter training run.

## Results

The model learns the vocabulary and general structure of financial news, but generated text can contain factual and numerical errors.

Training was done on a Google Colab NVIDIA T4 using float16 and checkpointing to handle session limits.

## Models

- Run 1 — [FinSLM-30M-LR3e-4-GA4](https://huggingface.co/mahadev-balla/FinSLM-30M-LR3e-4-GA4)
- Run 2 — [FinSLM-30M-LR1e-4-GA32](https://huggingface.co/mahadev-balla/FinSLM-30M-LR1e-4-GA32)
