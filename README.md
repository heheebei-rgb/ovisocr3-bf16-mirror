# OvisOCR3 BF16 权重镜像（GitHub 源码包分发）

[ATH-MaaS/OvisOCR3](https://huggingface.co/ATH-MaaS/OvisOCR3)（OCR 识别模型，apache-2.0，Qwen3.5-0.8B 底座，BF16 存储）权重的分块镜像，用于无法直连 HuggingFace 的内网环境。

## 下载与重建
1. 本仓库页面 **Code → Download ZIP**（约 1.7GB），解压
2. 在解压目录执行 `python3 merge_and_verify.py`（Python3 标准库，无需联网）
3. 脚本自动把 19 个分块合并回 `model.safetensors` 并做 sha256 全量校验
4. 完成后本目录即完整模型：权重 + tokenizer 全套 + 16 个 prompt 模板 + `document_crosspage.py` 推理脚本，transformers 可直接加载（原模型卡见 MODEL_CARD.md）

## 内容清单
- `chunks/main/` — model.safetensors 的 19 个 90MB 分块
- `MANIFEST.json` — 全部 34 个文件的 sha256 + 字节数
- `merge_and_verify.py` — 合并 + 校验脚本
- tokenizer：tokenizer.json / vocab.json / merges.txt / tokenizer_config.json
- config.json / generation_config.json / preprocessor_config.json / chat_template.jinja
- prompts/ 16 个任务模板 + assets/ 示例图
