# client
客户端项目使用Vue框架搭建，具体安装方法如下：
``` bash
# 安装Vue命令行工具
npm install --global vue-cli

# 安装一个新项目（此步骤省略）
npm install -g @vue/cli-init
vue init webpack my-project

# 安装依赖
cd 项目所在的文件夹
npm install

# 服务以热重载的方式运行在 localhost:8000
npm run dev

# 可能需要安装的依赖
npm install vue-cookies --save // cookies服务
npm install vue-resource --save // http服务
```