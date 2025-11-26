# hzsmkByBus
# 一键直达 `杭州市民卡·人才码·免费乘车码（青荷礼包）` 页面
一个自动跳转工具页，用于弱网环境下将杭州市民卡登录后的 `accessToken` 转换为杭州市人才系统的 `hzrckToken`，并跳转到`免费乘车码`页面。

此页面适用于通过 `GitHub Pages` 或 `Tencent EdgeOne Pages` 或 `CloudFlare Pages` 托管，并通过 URL 参数完成一次性跳转流程。

---

## ✨ 功能说明

页面加载后自动执行以下逻辑：

1. 接收 URL 中传入的 `token`（市民卡accessToken, 见下方使用方式）；
2. 请求接口 `https://open.iconntech.com/unifyUser/changeToken` 获取对应的 `channelToken`；
3. 用 `channelToken` 请求杭州市人才系统获取 `hzrckToken`；
4. 自动跳转到杭州市人才系统的乘车码页面：

```https://hzrck.hzzhdj.cn/exthtml/youngTalentCard/freeCoderide/#/byBus?token=hzrckToken```


---

## 🔗 使用方式

### URL 格式：

- ```https://ch3ngyz.github.io/hzsmkByBus/?token=xxxx```
或者
- ```https://hzsmk.ch3ng.top/?token=xxxx```

其中 `xxxx` 是你从`杭州市民卡`App登陆时，通过抓包`https://open.iconntech.com/unifyUser/loginFaceCheck`(返回体中)或`https://open.iconntech.com/unifyUser/queryUserByToken`(请求体中)获取的`accessToken`。
测试请求成功后，推荐使用Hermit将网页作为轻app放置在桌面快速打开，或使用浏览器功能`添加书签到桌面`。

### 📲 安装到桌面 (PWA)

本页面支持 PWA (Progressive Web App) 标准，可像原生 App 一样安装到桌面：

1. **打开页面**：使用 Chrome 浏览器打开带有 `token` 的链接。
2. **点击安装**：浏览器顶部地址栏右侧通常会显示“安装”图标，点击即可自动安装到桌面。
3. **手动安装**：如果未显示图标，请点击浏览器右上角菜单（⋮），选择“安装应用”或“添加到主屏幕”。
4. **快捷使用**：安装后，桌面会出现“杭州公交卡”图标，点击即可直接进入乘车页面，体验更佳。

---

## 🧩 详细特性

### 1. 智能缓存机制
- **加速加载**：页面会自动缓存 `channelToken` 和 `hzrckToken` 到本地 (`localStorage`)。
- **自动失效**：当缓存失效时，会自动尝试使用原有 `token` 重新获取，确保链路畅通。

### 2. 调试与日志
- **实时日志**：页面底部包含一个可折叠的日志控制台，记录详细的运行步骤和错误信息。
- **故障排查**：如果遇到问题，可以展开日志查看具体的 API 响应状态。

### 3. 缓存管理
- **手动清理**：日志面板中提供了“清除 ChannelToken”、“清除 HzrckToken”和“清除全部”按钮，方便在 Token 异常时重置状态。

### 4. 额度显示
- **实时查询**：跳转前会自动查询并显示当前的公交卡余额及有效期，方便确认权益状态。

---

## 🚫 错误处理

- 如果 URL 中未包含 `token` 参数，将提示：“缺少 token 参数”
- 如果任何一步失败（如 token 无效、接口响应异常），页面会显示具体错误原因

---

## 🛠️ 开发说明

本页面使用原生 HTML 编写，适合直接部署到 GitHub Pages：

- 主文件：`index.html`
- 无需构建或依赖打包工具
- 所有请求均为跨域接口，浏览器环境支持

---

## 📄 接口说明

1. `https://open.iconntech.com/unifyUser/changeToken`
    - 输入：appId + accessToken
    - 输出：channelToken（用于人才系统）

2. `https://talent.hzrcm.cn/smk_hztalent/front/app/home/getHzrckToken`
    - 输入：channelToken + channel（固定为 `smk_app`）
    - 输出：hzrckToken（人才系统登录令牌）

3. `https://hzrck.hzzhdj.cn/exthtml/youngTalentCard/freeCoderide/#/byBus?token=hzrckToken`
   - 输入：hzrckToken
   - 输出：乘车码页面
---

## 📢 免责声明

本工具仅供学习研究使用，请勿用于任何违反平台服务条款的用途。
