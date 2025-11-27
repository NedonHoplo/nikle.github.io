# 简单视频直播示例（含截图）

这是一个极简的 demo：使用浏览器的 getUserMedia + WebRTC 做主播与观众之间的 P2P 连接，使用 socket.io 做信令。页面也实现了“截图并下载”功能。

功能
- 成为主播：获取摄像头/麦克风并推流
- 成为观众：通过 WebRTC 与主播建立连接并观看
- 截图：主播可将当前视频帧截图并下载 PNG

快速运行（Windows PowerShell）

1. 在项目目录打开 PowerShell（本例目录为 repo 根，即包含 `server.js` 的文件夹）

```powershell
npm install
npm start
```

2. 在浏览器打开：

http://localhost:3000

3. 测试方法
- 在一个浏览器窗口（或一个设备）点击“成为主播”，允许摄像头权限。
- 在另一个浏览器窗口或另一个设备打开同样页面，点击“成为观众”。
- 主播可点击“截图并下载”保存当前画面。

注意事项与限制
- 这个 demo 使用 P2P（WebRTC）。主播需要与每个观众建立一个单独的 PeerConnection，适用于小规模示范测试。
- 若部署到公网，请使用 HTTPS（浏览器对 getUserMedia/WebRTC 在非安全上下文通常有限制）并根据需要添加 TURN 服务器以提高穿透能力。

下一步建议
- 添加 TURN 服务器配置以改善 NAT/防火墙场景
- 实现录制或云端转推（例如 RTMP）以支持大规模直播
