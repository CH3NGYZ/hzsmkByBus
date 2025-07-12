# hzsmkByBus

一个自动跳转工具页，用于将市民卡登录后的 `token` 转换为杭州市人才系统的 `hzrckToken`，并跳转到“免费乘车码”页面。

此页面适用于通过 GitHub Pages 托管，并通过 URL 参数完成一次性跳转流程。

---

## ✨ 功能说明

页面加载后自动执行以下逻辑：

1. 接收 URL 中传入的 `token`（市民卡登录令牌）；
2. 请求接口 `https://open.iconntech.com/unifyUser/changeToken` 获取对应的 `channelToken`；
3. 用 `channelToken` 请求杭州市人才系统获取 `hzrckToken`；
4. 自动跳转到杭州市人才系统的乘车码页面：

```https://hzrck.hzzhdj.cn/exthtml/youngTalentCard/freeCoderide/#/byBus?token=hzrckToken```


---

## 🔗 使用方式

### URL 格式：

```https://ch3ngyz.github.io/hzsmkByBus/?token=xxxx```


其中 `xxxx` 是你从市民卡系统获取的 token。

---

## 🚫 错误处理

- 如果 URL 中未包含 `token` 参数，将提示：“缺少 token 参数”
- 如果任何一步失败（如 token 无效、接口响应异常），页面会显示具体错误原因

---

## 🛠️ 开发说明

本页面使用原生 HTML + Axios 编写，适合直接部署到 GitHub Pages：

- 主文件：`index.html`
- 无需构建或依赖打包工具
- 所有请求均为跨域接口，浏览器环境支持

---

## 📄 接口文档说明

1. `https://open.iconntech.com/unifyUser/changeToken`

    - 输入：appId + token
    - 输出：channelToken（用于人才系统）

2. `https://talent.hzrcm.cn/smk_hztalent/front/app/home/getHzrckToken`

    - 输入：channelToken + channel 固定为 `smk_app`
    - 输出：hzrckToken（人才系统登录令牌）

---

## 📢 免责声明

本工具仅供学习研究使用，请勿用于任何违反平台服务条款的用途。
