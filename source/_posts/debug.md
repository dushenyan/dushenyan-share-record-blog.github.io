---
title: vscode多端调试
date: 2022-08-05 10:50:46
categories: vscode
cover: https://picx.zhimg.com/v2-9bc3b2159fc83f3c8146f4c215336962_r.jpg?source=1940ef5c
---

## 目录结构

```
├── node
│   └── index.js
├── parcel
│   ├── Post.ts
│   ├── Posts.tsx
│   ├── index.html
│   ├── index.tsx
│   ├── package.json
│   ├── postRepository.ts
│   └── yarn.lock
├── react-cra
│   ├── README.md
│   ├── package.json
│   ├── public
│   ├── src
│   └── yarn.lock
├── README.md
├── package.json
└── yarn.lock
```

## 调试配置

默认一般选项

```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "type": "chrome",
            "request": "launch",
            "name": "Debug React, TS, Parcel app in Chrome",
            "url": "http://localhost:1234/",
            "webRoot": "${workspaceFolder}/parcel",
            "pathMapping": {
                "__parcel_source_root": "${workspaceFolder}/parcel"
            },
              "skipFiles": [
                "${workspaceFolder}/parcel/node_modules/**/*.js",
                "<node_internals>/**/*.js"
            ]
        },
        {
            "type": "chrome",
            "request": "launch",
            "name": "Debug CRA web app in Chrome",
            "url": "http://localhost:3000",
            "webRoot": "${workspaceFolder}/react-cra"
        },
        {
            "type": "node",
            "request": "launch",
            "name": "Launch Toy Node Server",
            "skipFiles": [
                "<node_internals>/**"
            ],
            "program": "${workspaceFolder}/node/index.js"
        }
    ]
}
```


## 参考文档

[调试示例仓库](https://github.com/thekarel/debug-anything)

[langch配置文件](https://www.jianshu.com/p/d3c6e25ae815)
