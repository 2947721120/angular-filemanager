## angular-filemanager

一个非常聪明的文件管理器在材料设计风格与AngularJS开发的浏览器管理你的文件
 by [Jonas Sciangula Street](https://github.com/joni2back)

[![生成状态](https://travis-ci.org/joni2back/angular-filemanager.svg?branch=master)](https://travis-ci.org/joni2back/angular-filemanager)

### 支持
该项目下的自由许可。如果你想支持的角度，文件管理器开发或只是感谢它的主要维护者，通过支付啤酒，您可以通过点击下面的按钮进行捐款 [![Donate](https://www.paypal.com/en_GB/i/btn/btn_donate_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=XRB7EW72PS982) 


#### [尝试演示](http://angular-filemanager.zendelsolutions.com/)
---------
![](https://raw.githubusercontent.com/joni2back/angular-filemanager/master/screenshot.gif)

###特征
   - 多国语言（英语，中国语，西班牙语，俄语，葡萄牙语，法语，德语，斯洛伐克语，希伯来语，波斯语，波兰语，乌克兰语，土耳其语）
   - 多个模板（列表/图标）
   - 多文件上传
   - 多文件支持
   - 选择文件的回调为第三方应用程序
   - 搜索文件
   - 目录树导航
   - 复制，移动，重命名（交互式UX）
   - 删除，编辑，预览，下载
   - 文件权限（CHMOD的Unix风格）
   - 移动支持

### 去做
   - 拖放
   - Dropbox和谷歌驱动器兼容性
   - 扩展后端桥（PHP，Java和Python中，节点，.NET）
   - 迁移jQuery来本地或angular.element

### 后端API
[Read the docs](API.md)

---------

### 使用现有项目
**1) Install and use**
```bower install --save angular-filemanager```

**2) 在项目中包含的依赖**
```html
<!-- third party -->
  <script src="bower_components/angular/angular.min.js"></script>
  <script src="bower_components/angular-translate/angular-translate.min.js"></script>
  <script src="bower_components/jquery/dist/jquery.min.js"></script>
  <script src="bower_components/bootstrap/dist/js/bootstrap.min.js"></script>
  <link rel="stylesheet" href="bower_components/bootswatch/paper/bootstrap.min.css" />

<!-- angular-filemanager -->
  <link rel="stylesheet" href="dist/angular-filemanager.min.css">
  <script src="dist/angular-filemanager.min.js"></script>
```

**3) Use the angular directive in your HTML**
```html
<angular-filemanager></angular-filemanager>
```

---------

### 使用源文件，而不是minified js
```html
<!--注释如果您需要使用原始源代码
  <script src="src/js/app.js"></script>
  <script src="src/js/directives/directives.js"></script>
  <script src="src/js/filters/filters.js"></script>
  <script src="src/js/providers/config.js"></script>
  <script src="src/js/entities/chmod.js"></script>
  <script src="src/js/entities/item.js"></script>
  <script src="src/js/services/apihandler.js"></script>
  <script src="src/js/services/apimiddleware.js"></script>
  <script src="src/js/services/filenavigator.js"></script>
  <script src="src/js/providers/translations.js"></script>
  <script src="src/js/controllers/main.js"></script>
  <script src="src/js/controllers/selector-controller.js"></script>
  <link href="src/css/animations.css" rel="stylesheet">
  <link href="src/css/dialogs.css" rel="stylesheet">
  <link href="src/css/main.css" rel="stylesheet">
-->

<!-- 注释如果您需要使用原始源代码 -->
  <link href="dist/angular-filemanager.min.css" rel="stylesheet">
  <script src="dist/angular-filemanager.min.js"></script>
<!-- /如果你需要使用原始源代码注释 -->
```

---------

### 延伸配置文件
```html
<script type="text/javascript">
angular.module('FileManagerApp').config(['fileManagerConfigProvider', function (config) {
  var defaults = config.$get();
  config.set({
    appName: 'angular-filemanager',
    pickCallback: function(item) {
      var msg = 'Picked %s "%s" for external use'
        .replace('%s', item.type)
        .replace('%s', item.fullPath());
      window.alert(msg);
    },

    allowedActions: angular.extend(defaults.allowedActions, {
      pickFiles: true,
      pickFolders: false,
    }),
  });
}]);
</script>
```

---------

### 有助于
为了促进该项目可以简单地派生该回购协议。要建立一个缩小的版本，你可以简单地运行咕嘟咕嘟
任务 `gulp build`.缩小/丑化文件被创建在 `dist` folder.

### 版本
为了提高透明度到我们的发布周期，并在努力保持向后兼容性，角文件管理器下保持 [the Semantic Versioning guidelines](http://semver.org/).

### 版权与许可
在代码和文档发布 [the MIT license](https://github.com/joni2back/angular-filemanager/blob/master/LICENSE).


