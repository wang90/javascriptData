## Vue 开发中的模凌两可使用

### 绑定 background-image
```````
<div class="circular" v-bind:style="{ backgroundImage: { url(image) }"></div>
```````

### css 使用样式隔离
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
##### - 使用 scss
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

需在vue.config.js添加
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

### 利用vue.prototype绑定全局变量提示报错[在ts中的使用]
```````
// main.ts
Vue.prototype.$api = xxxx

// shims-vue.d.ts
import Vue from 'vue'
import VueRouter, { Route } from 'vue-router'
import { Store } from 'vuex'

declare module 'vue/types/vue' {
  interface Vue {
    $router: VueRouter;
    $route: Route;
    $store: Store<any>;
    // 以下是在main.ts中挂载到Vue.prototype上的变量
    $api: any;
  }
}
```````



