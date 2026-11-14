# OneCall-model-host

OneCall 语音识别使用的 sherpa-onnx 中文流式小模型托管仓库。

模型来源：`sherpa-onnx-streaming-zipformer-small-ctc-zh-int8-2025-04-01`（Hugging Face `csukuangfj/sherpa-onnx-streaming-zipformer-small-ctc-zh-int8-2025-04-01`）

## 下载

Release 资产：

```
model.zip
```

- 大小：约 19.2 MB
- 解压后：`model.int8.onnx` + `bbpe.model` + `tokens.txt`
- SHA-256：`5A54968B48CD90E4385F411CF9FACE7B31F5A7A6379D34C2CE6D4767CE7C4801`

## 用途

OneCall App 启动后按需下载到 `filesDir/voice_model/`，识别全程本地、不联网。