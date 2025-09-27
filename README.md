# Github 网站定时请求工具

（使用Claude Sonnet 4开发）

一个使用 GitHub Actions 定期访问网站的小工具，确保你关心的网站保持在线状态。

## ✨ 特性

- 🕐 定时访问（默认每小时一次）
- 🔒 隐私保护（网站地址不会在日志中暴露）
- 📊 详细的访问统计
- 🚀 完全免费（使用 GitHub Actions）
- ⚡ 支持手动触发

## 🛠️ 设置步骤

### 1. Fork 或下载这个项目

### 2. 配置 GitHub Secrets

在你的仓库中，进入 `Settings` → `Secrets and variables` → `Actions`，添加以下 Secrets：

#### 必需的 Secrets：

- **WEBSITES** (必需)
  ```
  https://example.com,https://google.com,https://github.com
  ```
  多个网站用逗号分隔

#### 可选的 Secrets：

- **USER_AGENT** (可选)
  ```
  Mozilla/5.0 (compatible; MyBot/1.0)
  ```

- **TIMEOUT** (可选)
  ```
  30
  ```
  请求超时时间（秒）

### 3. 调整执行频率（可选）

编辑 `.github/workflows/ping-websites.yml` 中的 cron 表达式：

```yaml
schedule:
  - cron: '0 * * * *'  # 每小时
  # - cron: '*/30 * * * *'  # 每30分钟
  # - cron: '0 */6 * * *'   # 每6小时
```

### 4. 启用 Actions

确保在仓库的 `Actions` 标签页中启用了 GitHub Actions。

## 📋 使用方法

1. **自动执行**: 根据设定的时间自动运行
2. **手动执行**: 在 Actions 页面点击 "Run workflow"
3. **查看日志**: 在 Actions 页面查看执行结果

## 🔒 隐私说明

- 网站地址存储在 GitHub Secrets 中，不会在日志中显示
- 日志只显示 "网站 #1"、"网站 #2" 等编号
- HTTP 状态码会显示，但不包含具体网址

## 📊 输出示例

```
🚀 开始访问网站...
⏱️  超时设置: 30秒
📡 正在访问网站 #1...
✅ 网站 #1 访问成功 (HTTP: 200)
📡 正在访问网站 #2...
✅ 网站 #2 访问成功 (HTTP: 200)

📊 执行结果统计:
   总计: 2 个网站
   成功: 2 个
   失败: 0 个
   成功率: 100%
```

## 🎯 注意事项

- GitHub Actions 有使用限制，不要设置过于频繁的执行
- 建议不要一次性监控太多网站
- 某些网站可能会限制自动化访问

## 🔧 自定义

你可以根据需要修改脚本：
- 添加更多的 curl 参数
- 增加邮件通知功能
- 添加 webhook 回调
- 记录响应时间等

Happy monitoring! 🎉

