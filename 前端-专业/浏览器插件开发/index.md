## 教程资源

视频

1. https://www.bilibili.com/video/BV1c84y18738

api

https://developer.chrome.com/docs/extensions/reference/api?hl=zh-cn

开发框架

1. plasmo
2. wxt

## 目录结构

- manifest.json：元数据/各种定义/权限声明
- serviceworker：处理并监听浏览器事件，可以使用浏览器全部api，不能和页面内容交互
- contentscript：读取/修改dom

## manifest.json

```json
{
   // 必须
  "manifest_version": 3,
  "name": "插件名称",
  "version": "1.0",
    
  "description": "插件描述",
  "author": "作者名"
  "icons": {
    "16": "images/icon-16.png",
    "32": "images/icon-32.png",
    "48": "images/icon-48.png",
    "128": "images/icon-128.png"
  },
  // 注册serviceworker后台脚本
  "background": {
    "service_worker": "service-worker.js"
  },
  "host_permissions": [
    "https://*/*"  
  ],
  // 可以根据不同网站注入不同js
  "content_scripts": [
    {
      "js": [
        "content-script.js"
      ],
      "matches": [
        "http://*.example.com//"
      ]
    }
  ],
  // 选项页面
  "options_ui": {
      "page": "options.html",
      "open_in_tab": true
  }
  // 图标配置
  "action": {
    "default_icon": {
      "16": "images/icon-16.png",
      "32": "images/icon-32.png",
      "48": "images/icon-48.png",
      "128": "images/icon-128.png"
    }
  },
  // 插件权限
  "permissions": ["scripting", "activeTab"]
}
```

## content-scripts

逻辑注入页面