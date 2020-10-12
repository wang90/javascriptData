## TypeScript 使用报错问题汇总

### 当使用window对象时候，出现问题
``````
# 使用 
window.webkit
# 解决
( window as any).webkit
``````
### 使用Promise返回
`````
function currentData(): Promise<{}> {
  return new Promise((resolve,reject)=>{
    // your code;
    resolve()
  })
}
`````
### 未正常安装使用ts三方库
``````
# 在d.ts文件下添加
declare module 'xxx'
``````
### 以.json结尾的文件引用报错
``````
# 在tsconfig.json文件添加
...
"compilerOptions":{
  ...
  "resolveJsonModule": true,
}
...
``````

