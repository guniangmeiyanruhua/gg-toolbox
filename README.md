# GGBond的工具箱

基于 [sistarry/toolbox](https://github.com/sistarry/toolbox) 的 `tool/vps-toolbox.sh` 裁剪复制，只保留 GG 需要的 5 个一级菜单，子功能执行代码与原仓库保持一致。主脚本的子脚本入口已改为拉取本仓库的子目录副本（见下）：

- **m1 系统设置**（编号 1-19）：更新系统、系统信息、修改 root 密码、root 登录管理、修改 SSH 端口、修改时区、时间同步、切换 v4/V6、开放所有端口、更换系统源、DD Debian13 / Windows、NAT 重装、DD 飞牛、修改语言、修改主机名、DNS 优化、一键优化、VPS 重启
- **m2 网络代理**（编号 20-41）：代理工具箱、FRP、EasyTier、ShellCrash、CF WARP、Tcpfit、BBR+TCP 调参、Socks5/HTTP、VLESS Reality、Snell、Shadowsocks、VLESS Encryption、Hysteria2、Xray-Argo、AnyTLS、nftables、Realm、转发面板、DDNS、流媒体 DNS 解锁、流量狗、流量监控
- **m3 网络检测**（编号 42-55）：NodeQuality、融合怪测试、YABS 测试、网络质量体检、IP 质量体检、硬盘质量体检、TcpQuality、简单回程测试、完整路由检测、流媒体解锁、三网测速、网络 PING/DNS 检测、检查 25 端口开放、网络工具箱
- **m10 更新卸载**（编号 77、88、99，原一级菜单 10）：自动更新、更新工具箱、卸载工具箱。已适配 GG 版：88 从本仓库更新 gg-toolbox.sh 到 /etc/gg-toolbox.sh；77 使用本仓库 `tool/toolboxupdates.sh`（已把下载源改成本仓库、更新目标改成 gg-toolbox.sh）
- **m7 系统管理**（编号 72-76、78-83，原一级菜单 7）：系统清理、重装系统、系统组件、开发环境、工作区管理、防火墙管理、Fail2ban、系统监控、添加 SWAP、DNS 管理、定时任务

主菜单在本精简版中重新排为 01-05 显示，子菜单编号保持原编号不变，避免与原脚本对照时错位。

## 子目录副本与上游同步

本仓库包含上游 4 个子目录的完整副本，共 502 个文件，主脚本的子脚本入口指向本仓库：

- `VPS/`（93 个，上游提交 a29f2f5 时点）
- `OS/`（64 个）
- `PROXY/`（113 个）
- `Docker/`（232 个）

同步方式：每天由 Muse 的定时任务对比上游 sistarry/toolbox：这 4 个子目录有更新就把新版文件推到本仓库并汇报；主脚本 gg-toolbox.sh 每天用 ~/workspace/gg-toolbox/build_gg_toolbox.py 从上游最新主脚本按裁剪规则（只留 m1/m2/m3/m7/m10、地址改本仓库、m10 用适配版）重新生成，有变化就覆盖本仓库的 gg-toolbox.sh 并汇报；子目录文件保持上游原样不改写，因此子脚本内部写死的、指向原仓库其他目录（如 Alpine、Panel、AI 等未复制目录）的调用仍走原仓库。

## 运行

一键拉取运行（自定义域名，免下载）：

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/guniangmeiyanruhua/gg-toolbox/main/gg-toolbox.sh)
```

一键拉取运行后会自动安装：脚本存到 `/etc/gg-toolbox.sh` 并创建 `n`/`N` 快捷指令（不覆盖原 toolbox 的 `m`/`M`），之后在任意终端输入 `n` 或 `N` 即可打开。已安装时不会重复安装；更新走菜单里的“更新工具箱”（88）。

备用（GitHub 原始地址）：

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/guniangmeiyanruhua/gg-toolbox/main/gg-toolbox.sh)
```

或先下载再运行：

```bash
curl -fsSL -o gg-toolbox.sh https://raw.githubusercontent.com/guniangmeiyanruhua/gg-toolbox/main/gg-toolbox.sh && bash gg-toolbox.sh
```


## 来源与许可

原项目：https://github.com/sistarry/toolbox （MIT License）。本仓库为个人精简复制版，子脚本版权归原作者所有。
