# SubBoost for LazyCat

[SubBoost](https://github.com/SubBoost/subboost) 的懒猫微服 LPK v2 移植。

SubBoost 是 Clash/Mihomo 订阅转换、增强和管理工具。通过 UI 可视化，一键实现链式代理、精确分流、防 DNS 泄露和多订阅聚合等高级功能。

## 服务

- `app`：SubBoost 2.8.1，监听容器端口 3000
- `db`：PostgreSQL 16，数据保存在 `/lzcapp/var/postgresql`
- `cron`：定时更新规则索引和订阅

内部运行密钥由 LazyCat `stable_secret` 自动生成。首次打开应用后，访问 `/login#setup-token=<安装时设置的初始设置令牌>` 创建管理员账号。

## 构建

```bash
lzc-cli project release -o dist/subboost.lpk
```

GitHub Actions 使用 SubBoost 镜像作为版本源，跟踪 `stable` 通道并通过镜像模式交付；只发布到喵喵商店，不发布到官方商店。

自动发布需要仓库或组织配置以下 GitHub Secrets：

- `APPSTORE_URL`
- `APPSTORE_TOKEN`
- `APP_ID`（可选）
- `PRIVATE_STORE_GROUP_CODES`（可选）
