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



## 동적 라우터 만들기 

```
[ pages > [id].js ]

// 0. pages 폴더 안에 위와 같은 형태의 파일을 만든다. 
import { useRouter } from "next/router"

export default ()=>{
    const router = useRouter()

    return(
        <>
            <h1>포스트 페이지지지ㅣ</h1>
            <p>포스트아이디: {router.query.id}</p>
        </>
    )
}
```

```
[ pages > index.js ]

import React, {useState, useEffect} from 'react'
import { useRouter } from 'next/link'
import Link from 'next/link'

export default function Home(){
  const [inputValue, setValue] = useState("")
  //1. import한 useRouter를 불러온다.
  const router = useRouter()
  
  //2. 버튼을 클릭하면 해당 페이지로 이동하는 핸들러 함수를 만들어준다. 
  const handleClick=(e)=>{
    e.preventDefault()
    router.push(inputValue)
  }
  
  return(
    <div>
      <main>
        <lable>id</lable>
        <input 
          value={inputValue} 
          onChange={(e)=>{
            setValue(e.target.value)}
          } 
        />
        //3. 버튼 원클릭 이벤트에 슝 넣어줌 끝! 
        <button onClick={handleClick}>동적 페이지 이동</button>
      </main>
    </div>
  )

}

```




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
