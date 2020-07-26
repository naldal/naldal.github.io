---

title: "인텔리제이 Loading component 오류 해결"
excerpt: "에러 해결법"

categories:

- intellij

toc: true
toc_sticky: true

---

![]({{ site.url }}{{ site.baseurl }}/assets/images/loading component.png){: .align-center}

가끔 인텔리제이를 켜다 보면 프로젝트를 로드하다 말고 멈추는 경우가 더러 있었다.

컴퓨터 재부팅을 하면 고쳐지긴 하는데 매번 껐다 켤 수는 없는 노릇이라 해결법을 찾았다.

[IntelliJ idea stucked on "loading project" screen](https://stackoverflow.com/questions/47626478/intellij-idea-stucked-on-loading-project-screen)

1. IDE는 닫지말고 프로젝트만 닫는다. (File - close project)
2. 로컬에 있는 프로젝트 파일로 가서 `.idea` 파일을 삭제한다.
3. 인텔리제이에서 프로젝트를 연다.
4. `File` 메뉴에서 `invalidate caches and restart` 한다.
5. 끝

![]({{ site.url }}{{ site.baseurl }}/assets/images/idea2.png){: .align-center}

실제로 `idea` 파일만 지워도 문제없이 잘 열리는 것을 확인했다.

![]({{ site.url }}{{ site.baseurl }}/assets/images/unnamed.jpg){: .align-center}