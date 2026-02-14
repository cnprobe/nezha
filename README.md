<div align="center">
  <br>
  <img width="360" style="max-width:80%" src="resource/static/brand.svg" title="哪吒监控 Nezha Monitoring">
  <br>
  <small><i>LOGO designed by <a href="https://xio.ng" target="_blank">熊大</a> .</i></small>
  <br><br>
<img alt="GitHub release (with filter)" src="https://img.shields.io/github/v/release/cnprobe/nezha?color=brightgreen&style=for-the-badge&logo=github&label=Dashboard-Compat">
  <br>
  <br>
  <p>:trollface: <b>Nezha Dashboard Compat</b>: Based on V0, Provide V1 Dashboard API.</p>
  <p>:trollface: <b>哪吒面板兼容版</b>: 基于 V0 版本提供 V1 的面板 API 。</p>
  <p>Forked from: <a href="https://github.com/Nezhahq/nezha/tree/v0-final">Nezhahq/nezha:v0-final</a></p>
</div>

## Usage / 用法

Just like original Nezha Monitoring, to install or upgrade from original version:

和原版Nezhahq大佬以及和Chenx-dust大佬的项目内容类似，主要是调整了一些简单的代码内容，若各位大佬认为内容有误或涉及侵权以及其他问题需要交流，可以通过私信或邮件告知，感激不尽.

```bash
curl -L https://raw.githubusercontent.com/cnprobe/nezha/V0/script/install.sh -o nezha.sh && chmod +x nezha.sh && sudo ./nezha.sh
```

Then follow the prompt. *English version temporarily not provided.*

然后跟随指引即可。*暂不提供英语版本。*

## Compatible API / 兼容 API

所有已实现的 v1 API 在文件 [compat_v1.go](https://github.com/cnprobe/nezha/blob/V0/cmd/dashboard/controller/compat_v1.go) 中。目前支持了：

- 前台界面的所有 API （包括 WebSocket）
- 后台界面的部分只读 API
  - 支持基于 API Key 的登录
  - 支持服务器、告警、通知的信息获取
  - 可以兼容 [hiDandelion/Nezha-Mobile](https://github.com/hiDandelion/Nezha-Mobile) 的大部分只读功能
- 关于鉴权
  - 基于 API Key 实现的鉴权
  - 支持模仿 `/api/v1/login` 接口实现登录
    - 账号：API Key 对应备注
    - 密码： API Key
  - 支持三种提供 API Key 的方式
    - Cookie: `nz-jwt` （v1 版本默认使用）
    - Header: `Authorization: Bearer <API Key>` （v1 版本 API 使用）
    - Header: `Authorization: <API Key>` （v0 版本 API 使用）
  - 强制设置网站 CookieName 为 `nz-jwt` 便于保证兼容性

## Acknowledge / 致谢

- [Nezhahq/nezha](https://github.com/Nezhahq/nezha): Original Nezha Dashboard. 原版哪吒面板。
- [chenx-dust/nezha-compat](https://github.com/chenx-dust/nezha-compat): 哪吒面板的V1版本API实现