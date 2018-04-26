# wepy-upload -- 小程序上传组件

## 简介:

包含功能：

1. 安卓/IOS统一图片选择控件(样式/功能)；
2. 自定义相机功能： 使用前置摄像头，前置拍照后图片翻转；
3. 图片压缩功能并可自定义尺寸；
4. 图片上传；

## 更新

- 1.0.3
    - 修复错误提示语法错误;
    - 优化文档说明；

## 使用姿势：

1. 引用:

`import MTUpload from 'wepy-upload'`;

2. 添加 `components`:

`components = { MTUpload }`; 

3. `template` 中使用:

```html
<MTUpload class="index-upload"
    text="上传图片"
    modelAlbumText="请从相册中选择正脸照"
    :useCustomizedCamera="useCustomizedCamera"
    :uploadConfig="uploadConfig"
    @start.user="uploadStart"
    @compress.user="uploadCompress"
    @success.user="uploadSuccess"
    @fail.user="uploadFail"
></MTUpload>
```

## 详细属性与事件

- uploadConfig: 图片上传配置，缺省时不进行上传
    - type: Object
    - default: {}
```js
    uploadConfig: {
        // 上传地址；
        api: {
            token: 'url',
            upload: 'url',
        },
        // 上传地址拼接；
        dataToImageUrl(data) {
            return imageUrl;
        },
    }
```

- useCustomizedCamera: 是否使用自定义相机；

    - type: Boolean
    - default: false

- uploadId: 组件id，会在success中原样传出，可用于标识

    - type: Number
    - default: 0

- bg: 按钮背景

    - type: String
    - default: ''

- text: 按钮文案；

    - type: String,
    - default: '',

- imageSpaceLimit: 上传图片大小限制；

    - type: String,
    - default: '10mb',

- imageSizeLimit: 上传图片压缩尺寸；

    - type: Number,
    - default: 800,

- imageQuality: 图片压缩比例；

    - type: Number,
    - default: 0.9,

- modelPhotoText:  底部弹窗相机文案；

    - type: String,
    - default: '拍照',

- modelAlbumText: 底部弹窗相册文案；

    - type: String,
    - default: '从手机相册选择',

- modelHideText: 底部弹窗取消文案；

    - type: String,
    - default: '取消',

### 事件

- @tap.user: 按钮点击时触发；
    - params: 无

- @start.user: 上传开始
    - filePath: 图片临时路径

- @compress.user: 压缩后的图片
    - path: 图片临时路径
    - width: 图片宽度
    - height: 图片高度
    - compressTime: 压缩耗时

- @success.user: 图片选择成功；
    - data: 服务端接口返回数据；
    - image: 图片路径
    - width: 图片宽度
    - height: 图片高度
    - uploadId: 组件id
    - uploadTime: 上传耗时

- @fail.user: 图片选择失败；
    - error: 错误对象；
    - type: 错误类型；
    - msg: 错误提示语；


