# OneCall-model-host

OneCall 语音识别使用的 sherpa-onnx 中文流式小模型托管仓库。

模型来源：`sherpa-onnx-streaming-zipformer-small-ctc-zh-int8-2025-04-01`（Hugging Face `csukuangfj/sherpa-onnx-streaming-zipformer-small-ctc-zh-int8-2025-04-01`）

## 下载链路（App 实际使用）

1. **manifest**：`https://cdn.jsdelivr.net/gh/idearthas/OneCall-model-host@main/manifest.json`（jsdelivr CDN 镜像 GitHub raw）
2. **模型 zip**：GitHub API 资产通道 `api.github.com → release-assets.githubusercontent.com`
3. **兜底**：`releases/latest/download/model.zip` 直链 + APK 内置 v1 指纹

## 模型更新流程（换新模型时）

1. 电脑侧打包新 zip，计算 SHA-256
2. 本仓库创建新 Release（tag 递增），上传 model.zip
3. 更新 `manifest.json`：`version` +1，写入新的 `sha256`（提交到 main 分支）
4. 刷新 CDN 缓存：浏览器访问 `https://purge.jsdelivr.net/gh/idearthas/OneCall-model-host@main/manifest.json`

完成后，App 内「删除模型 → 重新下载」即获取最新版，无需发版 App。

## manifest.json 字段

| 字段 | 说明 |
|---|---|
| `version` | 模型版本号（递增） |
| `model` | 模型名（记录用） |
| `url` | 备用直链（App 以 API 通道优先） |
| `sha256` | zip 指纹（App 下载后强校验） |
| `size` | 字节数（记录用） |

## 当前版本

- `model.zip`：19.23 MB，SHA-256 `5A54968B48CD90E4387F411CF9FACE7B31F5A7A6379D34C2CE6D4767CE7C4801`
- 解压后：`model.int8.onnx` + `bbpe.model` + `tokens.txt`

App 下载后放置于 `filesDir/voice_model/`，识别全程本地、不联网。