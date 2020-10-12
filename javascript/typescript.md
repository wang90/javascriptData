## typeScript 使用报错问题汇总

### 当使用window对象时候，出现问题
``````
# 使用 
window.webkit
# 解决
( window as any).webkit
``````
