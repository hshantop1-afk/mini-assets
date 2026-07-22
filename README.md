# mini-assets

瑰宝前端 H5 与微信小程序共用的静态图片发布仓库。运行时只发布和访问 `illust/` 下的 WebP 文件，当前统一使用固定 Git Tag：

```text
https://cdn.jsdelivr.net/gh/hshantop1-afk/mini-assets@<tag>/illust/<category>/<name>.webp
```

## 目录约定

- `illust/`：Git 跟踪的 WebP 发布文件，按业务场景分类。
- `png/illust/`：与 WebP 保持相同相对路径的本地 PNG 管理镜像，用于查找、比对和后续重新转换。
- `png/` 已写入 `.gitignore`，因为 PNG 文件通常明显大于 WebP，不属于 CDN 发布产物；提交它们会持续放大仓库历史和克隆体积。

## PNG 边界

PNG 目录只存在于当前本地工作区，删除仓库或重新克隆后不会恢复，需另行备份。部分 PNG 来自可追溯的原始 PNG，部分只是由现有 WebP 解码生成的管理镜像；后者不能视为原始无损母版。

发布新素材时，应同时检查 WebP 与 PNG 路径一致、图片尺寸一致，再提交 WebP，并按项目约定更新发布 Tag。复用已有 Tag 时需要额外验证 CDN 已刷新到新提交。
