### vue 常用代码块

#### 绑定background-image
```````
<div class="circular" v-bind:style="{ backgroundImage: { url(image) }"></div>
```````

#### css 使用样式隔离
##### - 使用 ::v-deep
```````
<style lang="less" scoped>
.file-textarea {
  flex: 1;
  .el-textarea,
  ::v-deep .el-textarea__inner {
    height: 100%;
  }
}
</style>
```````
###### - 使用scss
```````
<style lang="scss" scoped>
.file-textarea {
  flex: 1;
  .el-textarea,
  >>> .el-textarea__inner {
    height: 100%;
  }
}
</style>
```````
需在vue.config.js添加
```````
{
    test: /\.vue$/,
    loader: "vue-loader",
    options: {
        loaders: {
            scss: "vue-style-loader!css-loader!sass-loader"
        }
    }
}
```````
