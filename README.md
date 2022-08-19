# uni-custom-widget-template
>单个H5自定义组件示例（vue3技术栈），用于充当跨端自定义组件在编辑器端的使用和预览。

### 目录说明
- src: 自定义组件源码；
- preview: 自定义组件web预览模块（发布NPM自定义组件需要）；
- src/components: 存放自定义组件源码（vue3技术栈）；
- src/components/uni-info-card/uni-info-card.vue: 自定义组件内容文件，使用uniapp开发自定义组件请遵循[easycom组件规范](https://uniapp.dcloud.net.cn/component/#easycom%E7%BB%84%E4%BB%B6%E8%A7%84%E8%8C%83)；
- src/components/xxx/assets: 存放自定义组件组件静态资源，比如 css、img等，此处存放的静态资源会经过webpack构建；
- src/pages: 自定义组件预览展示页；
- amis.config.js: amis-widget-cli配置文件；

### 相关开发文档
- vue3开发文档：[https://v3.cn.vuejs.org/](https://v3.cn.vuejs.org/)
- 自定组件注册器：[vue3-aipage-widget](https://github.com/aisuda/vue3-aipage-widget)
- 自定义组件开发工具：[amis-widget-cli](https://github.com/aisuda/amis-widget-cli)

### 开发说明

1. **安装依赖**
```bash
$ npm i 或者 yarn
```

2. **preview: H5自定义组件预览模式（带热更新）**
> H5预览模式：用于本地预览H5自定义组件内容。
```bash
$ npm run preview
```

3. **linkDebug: 外链调试（爱速搭平台预览小程序自定义组件）**
> linkDebug模式：用于在爱速搭平台中预览和调试H5自定义组件。
```bash
$ npm run linkDebug
```

4. **build2lib: 构建自定义组件web预览模块**
> build2lib模式：用于构建发布到 npm 中的文件，默认存放到当前 preview/ 目录下；
```bash
$ npm run build2lib
```

5. **package.json添加自定义组件信息，导入组件扩展包时需要**
> package.json 中添加 aipage-widgets 字段，用于放置当前自定义组件信息，有这个 aipage-widgets 字段才能被识别为自定义组件扩展包。

```bash
  ...
    "aipage-widgets": [
    {
      "type": "uni-info-card", // 自定义组件类型，必填项，同一应用下不允许有重复的自定义组件类型
      "framework": "vue3", // 技术栈类型，必填项
      "description": "信息展示卡片", // 自定义组件描述，在编辑器左侧组件面板作为描述信息展示，必填项
      "entry": "/web/renderer.umd", // 自定义组件入口文件路径，必填项
      "files": [  // 自定义组件依赖资源文件路径，非必填项
        "/web/renderer.css"
      ],
      "editorPlugin": {  // amis-editor自定义插件信息
        "pluginEntry": "/web/plugin.umd", // 自定义插件的入口文件，必填项
        "tag": [  // 自定义插件的分类，必填项
          "uni小程序组件"
        ],
        "sort": 100, // 自定义插件的排序，非必填项
        "device": [ // 自定义组件支持的设备类型，必填项
          "mobile",
          "quickapp"
        ]
      }
    },
    ... // 其他自定义组件
  ],
  ...
```
6. **发布一个NPM组件扩展包**
> 需要确保package.json中的name值唯一，version值不重复。
```bash
$ npm publish
```

7. **发布到指定的NPM仓库**
> 打开NPM配置文件（src/.npmrc），配置为指定仓库地址即可。

### 配置项说明（amis-widget-cli）
[请查看amis-widget-cli](https://github.com/aisuda/amis-widget-cli)


