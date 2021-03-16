# 브라우저 렌더링
브라우저가 화면에 나타나는 요소를 렌더링할 때, 웹킷(Webkit)이나 게코(Gecko) 등과 같은 렌더링 엔진을 사용한다. 렌더링 엔진이 HTML, CSS, JavaScript로 렌더링할 때 CRF(Critical Rendering Path)라는 프로세스를 사용하며 다음 단계들로 이루어진다.

1. 렌더링 엔진은 우선 HTML을 파싱해 **DOM(Document Object Model) 트리를 구축**
2. CSS 파싱 후, **CSSOM(CSS Object Model) 트리 구축**
3. DOM과 CSSOM을 조합하여 **렌더 트리(Render Tree) 구축**
4. **렌더 트리 배치**. 뷰포트를 기반으로 렌더 트리의 각 노드가 가지는 정확한 위치와 크기를 계산(Reflow 단계)
5. **렌더 트리 그리기**. 계산한 위치/크기를 기반으로 UI 백엔드가 노드를 돌며 각 요소를 화면에 그림(Paint 단계)

## 참고
- [Naver, 브라우저는 어떻게 동작하는가?](https://d2.naver.com/helloworld/59361)
