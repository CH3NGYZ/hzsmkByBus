# hzsmkByBus

一个 GitHub Pages 页面，用于将 channelToken 转换为 hzrckToken 并跳转到杭州人才卡乘车码页面。

## 使用方法

https://ch3ngyz.github.io/hzsmkByBus/?channelToken=你的channelToken


系统将自动：

1. 请求杭州市人才系统接口，获取 `hzrckToken`；
2. 拼接跳转链接；
3. 自动跳转到人才乘车码页面。

## 示例

https://ch3ngyz.github.io/hzsmkByBus/?channelToken=ef45c5b750d04b51ba61d7fcec9ada34

## 故障排查

- 若页面提示 `缺少 channelToken 参数`，请确认 URL 是否带上 `?channelToken=xxx`
- 若提示获取失败，请稍后再试或检查 token 是否有效
