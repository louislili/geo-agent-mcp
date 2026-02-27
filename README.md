# GEO Agent MCP Server

这是一套专为接管 GEO Agent（AI 搜索引擎优化平台）产品库和落地页体系而设计的官方 模型上下文协议（MCP）。

通过将此服务连接到您的 AI Agent（如 Cursor、Cline、Windsurf 或 Claude Desktop），您可以直接对话让大模型自动为您撰写 SEO 优化的着陆页，并智能注入到您的云端工作区。

## 🚀 一键安装与配置

由于本服务采用最新的 Remote SSE 架构，**您无需在本地安装任何代码或 NPM 包**。只需要在您的客户端配置中加入一个远程端点即可。

### 获取您的 API 密钥
1. 登录 [GEO Agent 控制台](https://geo.yigather.com)
2. 在左侧菜单进入 **Skills** 页面，点击生成并获取您的专属 `geo_sk_...` 密钥。 

### Cursor IDE 配置方法
1. 打开 Cursor 设置 -> Features -> MCP
2. 点击 `+ Add New MCP Server`
3. 选择 Type 为 `SSE`
4. Name 填入 `geo-agent`
5. URL 填入: `https://geo.yigather.com/api/v1/mcp`
6. 在环境变量中添加鉴权头部：
   - Key: `Authorization`
   - Value: `Bearer geo_sk_xxxxx` (替换为您的实际密钥)

### Cline (VS Code) / Claude Desktop 配置文件
在对应客户端的 `mcp.json` / `claude_desktop_config.json` 中添加以下节点：

```json
{
  "mcpServers": {
    "geo-agent": {
      "command": "node",
      "args": ["-e", "console.error('Remote SSE servers are typically configured directly in the UI if supported (like Cursor/Windsurf). For CLI/file configs that do not yet support SSE natively, please refer to their specific SSE bridging documentation.')"],
      "env": {}
    }
  }
}
```
*(注：对于直接支持 SSE MCP URL 插入的客户端，直接配置 `https://geo.yigather.com/api/v1/mcp` 即可)*
