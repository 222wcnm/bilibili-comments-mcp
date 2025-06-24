# Bilibili 评论工具 (MCP)

一个基于 Model Context Protocol (MCP) 的 B 站视频评论获取工具，可批量获取评论并支持楼中楼回复。

## 快速开始

### 1. 安装依赖
```bash
npm install @modelcontextprotocol/sdk axios
```

### 2. 设置 Cookie
```bash
# 方式一：环境变量
export BILIBILI_COOKIE="your_bilibili_cookie_here"

# 方式二：直接在工具调用时传入
```

### 3. 配置客户端
在 MCP 客户端（如 Claude Desktop）的配置文件中添加：

```json
{
  "mcpServers": {
    "bilibili-comments": {
      "command": "node",
      "args": ["/path/to/bilibili_mcp.js"],
      "env": {
        "BILIBILI_COOKIE": "your_bilibili_cookie_here"
      }
    }
  }
}
```

### 4. 启动服务
```bash
node bilibili_mcp.js
```

## 工具功能

### `get_video_comments`
获取 B 站视频评论，支持分页和楼中楼回复。

**参数：**
- `bvid` / `aid` - 视频ID（二选一）
- `page` - 页码，默认1
- `pageSize` - 每页数量（1-49），默认20
- `sort` - 排序：0时间，1热度
- `includeReplies` - 是否包含楼中楼，默认true
- `cookie` - B站Cookie（可选）

**示例：**
```javascript
{
  "bvid": "BV1xx411c7mD",
  "page": 1,
  "pageSize": 20,
  "sort": 1,
  "includeReplies": true
}
```

## Cookie 获取

1. 登录 B 站网页版
2. 打开开发者工具 (F12)
3. 切换到 Network 标签
4. 刷新页面，找到任意请求
5. 复制 Request Headers 中的 Cookie 值

## 相关链接

https://github.com/SocialSisterYi/bilibili-API-collect