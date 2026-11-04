# dsh-plugin-market

DSH 插件市场索引（格式 1），供 DeepSeek Harness「插件 → 发现」作为索引源读取。

- 索引地址：<https://raw.githubusercontent.com/ytw1981/dsh-plugin-market/main/index.json>
- 格式定义：DSH `@deepseek-ai/dsh-plugin-market-index`（`format: 1`）
- 当前条目：`dsh-genui@0.3.2`、`dsh-pet@0.4.2`（均来自 npm）

## 如何加入「发现」

DSH → 插件 → 发现 → 添加索引源，粘贴上面的索引地址即可（也已在 profile 的 `plugin-market` 行中配置）。

## 如何新增条目

在 `index.json` 的 `plugins` 数组中追加一项：

```json
{
  "name": "<npm 包名>",
  "title": { "zh-cn": "中文名", "en": "English name" },
  "description": { "zh-cn": "中文描述", "en": "English description" },
  "repository": { "url": "https://github.com/<owner>/<repo>" },
  "metadata": { "category": "ui", "keywords": ["..."], "labels": ["featured"] },
  "versions": [
    {
      "version": "1.0.0",
      "publishTimestamp": 1793775154,
      "source": { "type": "npm" }
    }
  ]
}
```

注意：`version` 必须是精确 SemVer；`publishTimestamp` 是 Unix 秒；本地化语言 id 必须小写（`zh-cn`，不是 `zh-CN`）；`metadata` 里的 `category` / `labels` 必须先在顶层的 `metadata.categories` / `metadata.labels` 中声明。

Git 来源的条目形如：

```json
"source": { "type": "git", "url": "https://github.com/<owner>/<repo>", "commit": "<40 位小写 sha>", "path": "<仓库内的包子目录>" }
```
