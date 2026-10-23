# better-status-page-lzcapp

[BetterStatusPage](https://github.com/BElluu/BetterStatusPage) 的 LazyCat LPK 打包 —— 自托管状态页（Node 单容器）。

## 形态

- 单容器镜像：`ghcr.io/belluu/better-status-page`，端口 3000
- 镜像交付：mirror 模式（`ghcr.1ms.run/belluu/better-status-page:{tag}`），digest 校验开启
- 版本发现：GHCR 严格三段式 SemVer tag，排除 latest 与 legacy v 前缀
- 仅喵喵商店；仅 PC 平台

## 部署参数与密钥

| 项 | 说明 |
|------|------|
| `admin_email` / `admin_password` | 首次设置向导的管理员账号，登录/设置页自动填充 |
| `JWT_SECRET` | stable_secret 自动生成并保持稳定 |
| `VAULT_ENCRYPTION_KEY` | stable_secret 生成；变更会导致已存 vault 密钥不可读 |

## 持久化

- `/lzcapp/var/data` → `/app/data`（SQLite + uploads）
- `/lzcapp/var/backups` → `/app/backups`

healthcheck 沿用上游 `wget /health`。
