react-app脚手架   
npm install -g create-react-app   
create-react-app xxx 
npm start 启动

react-app没有webpack问题：
npm run eject
如果报错：
Remove untracked files, stash or commit any changes, and try again.
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! caiyun_push@0.1.0 eject: `react-scripts eject`
npm ERR! Exit status 1
npm ERR! 
npm ERR! Failed at the caiyun_push@0.1.0 eject script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.

npm ERR! A complete log of this run can be found in:
npm ERR!     /Users/wang90/.npm/_logs/2019-07-27T06_35_39_275Z-debug.log
属于没有提交任何内容，需要
git add .
git commit -m 'Saving before ejecting'
npm run eject
