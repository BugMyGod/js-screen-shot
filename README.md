## 原插件js-web-screen-shot
#js-web-screen-shot · [![npm](https://img.shields.io/badge/npm-v1.1.2-2081C1)](https://www.npmjs.com/package/js-web-screen-shot) 

## 修改内容
```
增加参数containerStyle，targetId
```
## 插件安装
```bash
yarn add js-web-screen-shot2

# or

npm install js-web-screen-shot2 --save
```

### import形式使用插件
* 在需要使用截屏插件的业务代码中导入插件
```javascript
import ScreenShort from "js-web-screen-shot2";
```
* 在业务代码中使用时实例化插件即可
```javascript
new ScreenShort();
```
> ⚠️注意：实例化插件时一定要等dom加载完成，否则插件无法正常工作。
### cdn形式使用插件
* 将插件的`dist`文件夹复制到你的项目中
* 使用`script`标签引入dist目录下的`screenShotPlugin.umd.js`文件
```javascript
<script src="./screenShotPlugin.umd.js"></script>
```
* 在业务代码中使用时实例化插件即可
```javascript
    // 截图确认按钮回调函数
    const callback = (base64) =>{
      console.log(base64);
    }
    new screenShotPlugin({enableWebRtc: false, completeCallback: callback, containerStyle: containerStyle, targetId: id});
```
> ⚠️注意：实例化插件时一定要等dom加载完成，否则插件无法正常工作。

### 参数说明
截图插件有一个可选参数，它接受一个对象，对象每个key的作用如下:
* `enableWebRtc` 是否启用webrtc，值为`boolean`类型，值为`false`则使用`html2canvas`来截图
* `completeCallback` 截图完成回调函数，值为`Function`类型，最右侧的对号图标点击后会将图片的base64地址回传给你定义的函数，如果不传的话则会将图片的base64地址放到`sessionStorage`中，你可以通过下述方式拿到他：
```javascript
sessionStorage.getItem("screenShotImg");
```
*`containerStyle` 自定义截图范围，值为`Object ==> { width:number, height:number }`
*`targetId` 自定义截图目标id，值为`String ==> 'id'`
