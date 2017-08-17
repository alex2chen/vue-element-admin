## 前言
之前在公司用了Vue + Element组件库做了个后台管理系统，基本很多组件可以直接引用组件库的，但是也有一些需求无法满足。像图片裁剪上传、富文本编辑器、图表等这些在后台管理系统中很常见的功能，就需要引用其他的组件才能完成。从寻找组件，到使用组件的过程中，遇到了很多问题，也积累了宝贵的经验。所以我就把开发这个后台管理系统的经验，总结成这个后台管理系统解决方案。
该方案基于vue.js,使用vue-cli脚手架快速生成项目目录，作为一套多功能的后台框架模板，适用于绝大部分的后台管理系统（Web Management System）开发。

## 功能
- [x] Element UI
- [x] 登录/注销
- [x] 表格
- [x] 表单
- [x] 图表 :bar_chart:
- [x] 富文本编辑器
- [x] markdown编辑器
- [x] 图片拖拽/裁剪上传
- [x] 支持切换主题色 :sparkles:


## 目录结构介绍
	|-- build                            // webpack配置文件
	|-- config                           // 项目打包路径
	|-- src                              // 源码目录
	|   |-- components                   // 组件
	|       |-- common                   // 公共组件
	|           |-- Header.vue           // 公共头部
	|           |-- Home.vue           	 // 公共路由入口
	|           |-- Sidebar.vue          // 公共左边栏
	|		|-- page                   	 // 主要路由页面
	|           |-- BaseCharts.vue       // 基础图表
	|           |-- BaseForm.vue         // 基础表单
	|           |-- BaseTable.vue        // 基础表格
	|           |-- Login.vue          	 // 登录
	|           |-- Markdown.vue         // markdown组件
	|           |-- MixCharts.vue        // 混合图表
	|           |-- Readme.vue           // 自述组件
	|           |-- Upload.vue           // 图片上传
	|           |-- VueEditor.vue        // 富文本编辑器
	|           |-- VueTable.vue         // vue表格组件
	|   |-- App.vue                      // 页面入口文件
	|   |-- main.js                      // 程序入口文件，加载各种公共组件
	|-- .babelrc                         // ES6语法编译配置
	|-- .editorconfig                    // 代码编写规格
	|-- .gitignore                       // 忽略的文件
	|-- index.html                       // 入口html文件
	|-- package.json                     // 项目及工具的依赖配置文件
	|-- README.md                        // 说明

## 安装步骤 ##
	git clone https://github.com/alex2chen/vue-element-admin.git
	cd manage-system										
	npm install	

	// 本地开发，访问 http://localhost:8080
	npm run dev

	// 构建生产
	npm run build

## 组件使用说明与演示

### element-ui ###
基于vue.js2.0 UI组件库[element](http://element.eleme.io/#/zh-CN/component/layout)

### vue-datasource ###
动态创建表格的服务端组件[vue-datasource](https://github.com/coderdiaz/vue-datasource)

### Vue-Quill-Editor ###
基于Quill、适用于Vue2的富文本编辑器[vue-quill-editor](https://github.com/surmon-china/vue-quill-editor)

### Vue-SimpleMDE ###
Markdown Editor组件[Vue-SimpleMDE](https://github.com/F-loat/vue-simplemde)

### Vue-Core-Image-Upload ###
一款轻量级的vue上传插件，支持裁剪[Vue-Core-Image-Upload](https://github.com/Vanthink-UED/vue-core-image-upload)

### vue-echarts-v3 ###
eCharts.js3的图表组件[vue-echarts-v3](https://github.com/xlsdg/vue-echarts-v3)

## 注意事项 ##
### 一、如果我不想用某些组件而不影响到其他功能呢？
举个栗子，我不想用 vue-datasource
- Step1：删除该组件的路由，在目录 src/router/index.js 中，找到引入改组件的路由，删除下面这段代码。
```JavaScript
{
    path: '/vuetable',
    component: resolve => require(['../components/page/VueTable.vue'], resolve)     // vue-datasource组件
}
```
- Step2：删除引入该组件的文件。在目录 src/components/page/ 删除 VueTable.vue 文件。
- Step3：删除该页面的入口。在目录 src/components/common/Sidebar.vue 中，找到该入口，删除下面这段代码。
```HTML
<el-menu-item index="vuetable">Vue表格组件</el-menu-item>
```
- Step4：卸载该组件。执行以下命令：

	npm un vue-datasource -S

### 二、如何切换主题色呢？ ###

- Step1：打开src/main.js 文件，找到引入element 样式的地方，换成浅绿色主题
```javascript
import 'element-ui/lib/theme-default/index.css';    // 默认主题
// import '../static/css/theme-green/index.css';       // 浅绿色主题
```
- Step2：打开src/App.vue 文件，找到 style 标签引入样式的地方，切换成浅绿色主题。
```javascript
@import "../static/css/main.css";
@import "../static/css/color-dark.css";     /*深色主题*/
/*@import "../static/css/theme-green/color-green.css";   !*浅绿色主题*!*/
```
- Step3：打开src/components/common/Sidebar.vue 文件，找到 el-menu 标签，把 theme="dark" 去掉即可

## 项目截图 ##
### 默认皮肤 ###
![Image text](https://github.com/lin-xin/manage-system/raw/master/screenshots/wms1.png)

### 浅绿色皮肤 ###
![Image text](https://github.com/lin-xin/manage-system/raw/master/screenshots/wms2.png)
