# movie-example

> 참조 URL: https://medium.com/hivelab-dev/vue-express-mysql-part1-98f68408d444

### Step1. 프론트엔드 개발 환경 세팅 (Vue.js)

```
npm install -g yarn 
npm install -g @vue/cli 
vue create frontend // frontend 폴더 생성
cd frontend
npm run serve //서버 실행

http://localhost:8080/
```

### Step2. 백엔드 개발환경 세팅 (Express)

```
npm install -g express-generator
express --view=pug backend // backend 폴더 생성
cd backend 
npm install 
npm start // 서버 실행

http://localhost:3000/
```

### Step3. 백엔드와 연동

```
./frontend/vue.config.js 생성

module.exports = { 
  devServer: { ① api 요청이 있을때 어디에서 처리할지를 설정
    proxy: { 
      '/api': { 
        target: 'http://localhost:3000/api',
        changeOrigin: true, 
        pathRewrite: { 
          '^/api': ''
        } 
      } 
    } 
  },
  outputDir: '../backend/public',  ② 배포 파일의 위치를 지정
}

front에서 npm run build
http://localhost:3000/
```
