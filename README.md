# mini-assets

瑰宝前端 H5 与微信小程序共用的静态图片发布仓库。运行时只发布和访问 `illust/` 下的 WebP 文件：

```text
https://cdn.jsdelivr.net/gh/hshantop1-afk/mini-assets@<tag>/illust/<category>/<name>.webp
```

## 目录约定

- `illust/`：Git 跟踪的 WebP 发布文件，按业务场景分类。
- `png/illust/`：与 WebP 保持相同相对路径的本地 PNG 管理镜像，用于查找、比对和后续重新转换。
- `png/` 已写入 `.gitignore`，因为 PNG 文件通常明显大于 WebP，不属于 CDN 发布产物；提交它们会持续放大仓库历史和克隆体积。

## PNG 边界

PNG 目录只存在于当前本地工作区，删除仓库或重新克隆后不会恢复，需另行备份。部分 PNG 来自可追溯的原始 PNG，部分只是由现有 WebP 解码生成的管理镜像；后者不能视为原始无损母版。

## 发布规则

1. 新增或修改素材时，按 `assets-YYYY.MM.DD.N` 创建发布 Tag；`N` 每天从 `1` 开始递增。
2. 发布 Tag 创建后不可移动、覆盖或删除，避免 CDN 与小程序沙盒继续命中旧内容。
3. 前端清单为每张素材分别记录路径和 Tag。只有本批新增或修改的素材切换到新 Tag，未修改素材继续使用原 Tag。
4. 发布前检查 PNG 与 WebP 路径一致、尺寸一致、透明通道有效；发布后检查 CDN 状态、内容类型和 SHA-256。
5. 素材稳定后可创建语义化稳定版本，例如 `assets-v1.0.0`。
