# Blog 작성 가이드 문서

### 글 작성일자
* 설명: 마크다운 파일 내에서 지정할 작성 식간
* 단축: ;dtkr;
* 포맷: 2019/02/14 18:55:13 +09:00
```
2020-04-23 08:24:15 +09:00
```

### 글 해시값 (지정시간)
* 설명
    > 현재 시간을 기본값으로 제공해주고 지정된 "년-월-일 시:분:초" 값으로 MD5 해시값을 생성하고 포맷에 맞춰 파일명으로 사용할 문자열을 반환
    > 시간을 수정해서 특정 시점에 해당하는 해시값을 생성 가능
    > 년-월-일-년월일시분초-MD5
* 단축: ;inmd5;
* 포맷: 2019-02-14-20190214185525-5db75118bede859338ec6b48d5519bbc

### 글 해시값 (현재시간)
* 설명
    > 현재의 "년-월-일 시:분:초" 값으로 MD5 해시값을 생성하고 포맷에 맞춰 파일명으로 사용할 문자열을 반환
    > 년-월-일-년월일시분초-MD5
* 단축: ;dtmd5;
* 포맷: 2019-02-14-20190214185525-5db75118bede859338ec6b48d5519bbc

### 해시값 사용
* 해시값: 2019-02-14-20190214185525-5db75118bede859338ec6b48d5519bbc
* 파일 경로: _posts/2019-02-14-20190214185525-5db75118bede859338ec6b48d5519bbc.md
* 이미지 경로: assets/images/5db75118bede859338ec6b48d5519bbc
```
2020-04-23-20200423082415-f66b02dc2f58cc46226ea57e313fe2ca
_posts/2020-04-23-20200423082415-f66b02dc2f58cc46226ea57e313fe2ca.md
assets/images/f66b02dc2f58cc46226ea57e313fe2ca
```

### 이미지 설정
* 지연된 이미지 로딩과 썸네일 이미지 표시 기능을 제공하고 클릭시 원본 이미지를 보여주도록 이미지 태그 적용
* 예제
    - 링크 텍스트: 사용자가 보게될 텍스트, `차량관련정보`
    - 초기 이미지: 최초 로딩시 내용이 없는 이미지로 지정, `assets/images/blank.png`
    - 표시 이미지: 지연 로딩으로 보여주기 위해 가로 840px 크기로 축소된 이미지, `assets/images/5db75118bede859338ec6b48d5519bbc/001.840.jpg`
    - 원본 이미지: 클릭시 보여줄 원본 이미지, `assets/images/5db75118bede859338ec6b48d5519bbc/001.png`
    - 캡션 텍스트: 이미지 설명으로 보여줄 텍스트 `차량관련정보`
```
[![Privilege Escalation](assets/images/blank.png){:data-echo="assets/images/f66b02dc2f58cc46226ea57e313fe2ca/001.840.jpg"}](assets/images/f66b02dc2f58cc46226ea57e313fe2ca/001.png){:caption="권한 상승"}
[![Powershell.exe](assets/images/blank.png){:data-echo="assets/images/f66b02dc2f58cc46226ea57e313fe2ca/001.840.jpg"}](assets/images/f66b02dc2f58cc46226ea57e313fe2ca/001.png){:caption="파워쉘"}
``` 
* 이미지 변환 스크립트, 숫자로 구성된 png 파일을 가로 840px 크기의 jpg 포맷으로 변환
```
cd "assets/images/f66b02dc2f58cc46226ea57e313fe2ca"
for f in $(find -E . -depth 1 -regex ".*[0-9]+\.(png)"); do convert "${f}" -resize 840x\> -set filename:newwidth '%W' "${f%.*}.%[filename:newwidth].jpg" ; done
```

### 테스트
```
cd ~/Projects/kiros33.github.com/
JEKYLL_ENV=development bundle exec jekyll serve --limit_posts 5
```

### 빌드
```
JEKYLL_ENV=production bundle exec jekyll build
```

### 소스 저장
 ```
cd ~/Projects/kiros33.github.com/
git add .
git commit -m 'commit' && git push
cd ~/Projects/kiros33.github.io/
git add .
git commit -m 'commit' && git push
```