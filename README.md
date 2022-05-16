# 2022.05.16 : Next.js 

- 서버사이드 렌더링 지원 
- seo적용에 수월함 


```
//설치
npx create-next-app 프로젝트명

//시작
npm run dev 
```

**create-next-app으로 설치하면 
1. 컴파일과 번들링이 자동으로 된다.(webpack과 bable)
2. 자동 리프레쉬 기능으로 수정하면 화면에 바로 반영됩니다. 
3. 서버사이드 렌더링이 지원됩니다. 
4. 스태틱 파일을 지원합니다. 

pages폴더 안에 파일을 만드면 자동으로 router처리가 된다. 


```
pages > about.js 

export default function About(){
  return <div>about</div>
}

```
*** http://localhost:3000/about 접속



```
pages > view > [id].js

export default function view(){
  return <div>id</div>
}
```
*** http://localhost:3000/view/3 :: id를 동적으로 사용할 수 있음

** Next js 모든 페이지 사전 렌더링 (Pre-rendering)
더 좋은 퍼포먼스
검색엔진최적화(SEO)
1. 정적 생성 
2. Server Side Rendering(SSR, Dynamic Rendering)

차이점은 언제 html 파일을 생성하는가.

[정적생성]
- 프로젝트가 빌드하는 시점에 html파일들을 생성 
- 모든 요청에 재사용
- 퍼포먼스 이유로, 넥스트 js는 정적 생성을 권고
- 정적 생성된 페이지들은 CDN에 캐시
- getStaticProps / getStaticPaths 
-
[서버사이드 렌더링]은 매 요청마다 html을 생성
- 항상 최신 상태 유지
- getServerSideProps
