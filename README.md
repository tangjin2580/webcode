# webcode

一组 HTTP 状态码 / 边缘节点（CDN）错误页与提示页模板。纯静态 HTML，可直接用于 Web 服务器、反向代理或 CDN（如 Cloudflare）的自定义错误页场景。

## 页面清单

| 文件 | 状态码 | 说明 |
|------|--------|------|
| `403.html` | 403 | Forbidden · 禁止访问 |
| `404.html` | 404 | Page Not Found · 页面不存在 |
| `404-app.html` | 404 | App Not Found · 应用不存在 |
| `429.html` | 429 | Too Many Requests · 请求过于频繁 |
| `465.html` | 465 | Waiting Room · 等待室 |
| `466.html` | 466 | 应用维护中 |
| `467.html` | 467 | 身份认证 |
| `468.html` | 468 | 人机验证 |
| `502.html` | 502 | Bad Gateway · 网关错误 |
| `504.html` | 504 | Gateway Timeout · 网关超时 |

> 说明：`465` / `466` / `467` / `468` 为部分 CDN / 边缘平台使用的自定义状态码，分别对应等待室、维护、认证与人机验证场景。

## 使用方式

- **本地预览**：直接用浏览器打开对应的 `.html` 文件即可。
- **Nginx 自定义错误页**示例：

  ```nginx
  error_page 404 /404.html;
  error_page 502 504 /502.html;

  location = /404.html {
      root /path/to/webcode;
      internal;
  }
  ```

- **Cloudflare 自定义页面**：在对应的 Custom Pages / Waiting Room 设置中上传对应 HTML 即可。

## 目录结构

```text
webcode/
├── .gitignore          # 忽略 IDE 配置与系统文件（.idea/ 等）
├── README.md
├── 403.html            # 禁止访问
├── 404.html            # 页面不存在
├── 404-app.html        # 应用不存在
├── 429.html            # 请求过于频繁
├── 465.html            # 等待室
├── 466.html            # 应用维护中
├── 467.html            # 身份认证
├── 468.html            # 人机验证
├── 502.html            # 网关错误
└── 504.html            # 网关超时
```

## 备注

- 所有页面均为独立静态文件，无外部运行时依赖。
- IDE 配置（`.idea/` 等）已被 `.gitignore` 忽略，不会进入版本库。
