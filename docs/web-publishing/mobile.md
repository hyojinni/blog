---
layout: default
title: Mobile
parent: Web Publishing
nav_order: 90
---

# Mobile
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---

### Meta Tag

##### 모바일 웹페이지를 가로크기에 맞추기

  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no, target-densitydpi=medium-dpi">
  ```
  - `width=device-width`{:.property}  플랫폼 가로 크기에 맞춤
  - `initial-scale`{:.property}  확대비율
  - `maximum-scale`{:.property}  최대확대비율
  - `minimum-scale=1.0`{:.property}  최소축소비율
  - `user-scalable`{:.property}  사용자에 의한 화면확대 가능여부 (yes / no)

---


### Tip

##### 화면 회전시 폰트사이즈 고정
  ```css
  {-webkit-text-size-adjust:none}
  ```

##### PC, MOBILE 구별하기
  ```js
  // 모바일 위주로 구별
  var mobileKeyWords = new Array('iPhone', 'iPod', 'BlackBerry', 'Android', 'Windows CE', 'Windows CE;', 'LG', 'MOT', 'SAMSUNG', 'SonyEricsson', 'Mobile', 'Symbian', 'Opera Mobi', 'Opera Mini', 'IEmobile');
    for (var word in mobileKeyWords) {
      if (navigator.userAgent.match(mobileKeyWords[word]) != null) {
        window.location.href = "이동할 경로";
        break;
    }
  }


  // PC, MOBILE 구별
  function deviceCheck() {
      // 디바이스 종류 설정
      var pcDevice = "win16|win32|win64|mac|macintel";
  
      // 접속한 디바이스 환경
      if ( navigator.platform ) {
          if ( pcDevice.indexOf(navigator.platform.toLowerCase()) < 0 ) {
              console.log('MOBILE');
          } else {
              console.log('PC');
          }
      }
  }
  ```

##### 이미지를 해상도에 맞게 조절할 경우

```css
img {max-width:100%;}
```

##### form 요소의 기본속성을 초기화하는 방법
  ```css
  border-radius:0px 0px; /* 아이폰의 input 라운드 초기화 */
  -webkit-appearance:none; /* form 요소의 디바이스 기반 스타일 초기화 */
  ```

##### 전화번호 링크만 없앨때
  ```html
  <meta name="format-detection" content="telephone=no" />
  ```

##### 전화번호,이메일,지도 자동링크 방지
  ```html
  <meta name="format-detection" content="telephone=no, address=no, email=no" />
  ```

##### 유튜브영상 반응형 사이즈로 가져오기
```css
.video-container {
  position: relative;
  padding-bottom: 56.25%;
  padding-top: 30px;
  height: 0;
  overflow: hidden;
}

.video-container iframe,
.video-container object,
.video-container embed {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
```

```html
<div class="video-container">
  <iframe src="https://www.youtube.com/embed/9ZfN87gSjvI?wmode=transparent;rel=0&amp;showinfo=0;autoplay=0;vq=hd1080;autohide;" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen ></iframe>
</div>
```

* 자바스크립트를 활용

```js

//최초 로드 시 iframe 높이값 비율에 맞게 세팅
var $videoIframe = document.getElementById('video');
var responsiveHeight = $videoIframe.offsetWidth * 0.5625;
$videoIframe.setAttribute('height', responsiveHeight);

//브라우저 리사이즈 시 iframe 높이값 비율에 맞게 세팅
window.addEventListener('resize', function(){
    responsiveHeight = $videoIframe.offsetWidth * 0.5625;
    $videoIframe.setAttribute('height', responsiveHeight);
});
```

---

## 참고링크
- [PC, MOBILE 구별하기](https://studyhardgogo.tistory.com/139){:target="_blank"}
- [Responsive Youtube Embed](https://www.avexdesigns.com/blog/responsive-youtube-embed){:target="_blank"}
- [유튜브(Youtube) 영상 비율에 맞게 (반응형 사이즈)로 가져오기](https://code-study.tistory.com/35){:target="_blank"}