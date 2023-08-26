# 깃헙 github pages 에 배포하기

```bash
npm run build
```

build 후 생성된 dist 를 깃헙에 올리면 배포 끝!

```bash
// gh-pages 안에 dist 를 -d 복사해서 넣겠다
npx gh-pages -d dist
```

gh-pages 브런치가 자동생성되고 setting - pages root 브런치가 gh-pages 로 자동설정되게된다.

setting - action 에서 배포 진행 상황을 확인할수있다.

**그런데 하얀 화면만 표시가 된다.**
리소스 주소가 서브 디렉토리 기준이라 그렇다.

**vite.config.js**
아래 defineConfig 의 주소를 내 깃헙 레포 이름로 변경해준다.

```jsx
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import jsconfigPaths from "vite-jsconfig-paths";

// https://vitejs.dev/config/
export default defineConfig({
  // 여기서 내 깃헙 레포 이름을 똑같이 적어준다
  base: "/TodoList_react/",
  plugins: [react(), jsconfigPaths()],
});
```

배포 후 수정사항이 있을때는 아래 명령어를 반복해주면 된다

```bash
npm run build
npx gh-pages -d dist
```

참고: 캐쉬 강력하게 지우기
`ctrl + shift + R`
