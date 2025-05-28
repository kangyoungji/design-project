# Designdigit
> skill :
GSAP, ScrollTrigger, Swiper ![JavaScript](https://img.shields.io/badge/-JavaScript-dc8d2d?style=flat-square&logo=javascript&logoColor=ffffff) ![HTML](https://img.shields.io/badge/-HTML-F05032?style=flat-square&logo=html5&logoColor=ffffff) ![CSS](https://img.shields.io/badge/-CSS-007ACC?style=flat-square&logo=css3) 

> 반응형 : 데스크탑, 탭, 모바일  

> https://project1-git-main-yeongjis-projects.vercel.app/

✅ Point
------------
✔ 마우스 이벤트 구현  
✔ TOP 버튼 구현

----------------------------------------

## 1. 마우스 이벤트 구현

> 슬라이더 부분에 마우스를 올리면 그 부분에서만 viewmore이라는 새로운 커서가 나오도록 이벤트를 구현했습니다. 

![Image](https://github.com/user-attachments/assets/bfea5d69-d9f1-4b87-82f0-6aa921fd4b57) 


![HTML](https://img.shields.io/badge/-HTML-F05032?style=flat-square&logo=html5&logoColor=ffffff)
```
<div id="custom-cursor">
  <div class="custom-hover-circle"></div>
</div>
<div id="custom-cursor-text">
  <div class="custom-hover-text"><span class="serif">View More</span></div>
</div>
<div id="page-top">
  <button type="button" class="btn-top"><span class="serif">TOP</span></button>
</div>
```
>HTML에서 커스텀 커서와 관련된 요소를 정의하였습니다. 커서의 모양과 함께 사용자에게 정보를 제공할 수 있는 텍스트를 포함한 구조를 설정했습니다.
>CSS를 사용하여 커서의 디자인을 세밀하게 조정하였습니다. 원형 커서와 텍스트 요소의 스타일을 설정하여, 사용자가 마우스를 올렸을 때 직관적인 인터페이스를 제공합니다. 이 단계에서 색상, 크기, 위치 등을 조정하여 전체적인 사용자 경험을 한층 개선했습니다.  





![JavaScript](https://img.shields.io/badge/-JavaScript-dc8d2d?style=flat-square&logo=javascript&logoColor=ffffff)
```

let customHover=document.querySelectorAll(".custom-hover");

	document.body.addEventListener("mousemove", function(e){
		gsap.to("#custom-cursor, #custom-cursor-text", {
			x: e.clientX,
			y: e.clientY,
			duration: 1.2,
			ease: Power3.easeOut
		});
	});
```
>gsap.to() 메서드를 사용해 커서와 관련된 텍스트 요소가 부드럽게 이동하도록
>설정하였고 Power3.easeOut 이징 함수를 통해 자연스러운 애니메이션 효과를 주었습니다. 

```
	customHover.forEach(function(item){
		item.addEventListener("mouseenter", function(){
			gsap.to(".custom-hover-circle, .custom-hover-text", {
				width: "100%",
				height: "100%",
				opacity: 1,
				duration: 0.3,
				ease: Power3.easeOut
			});
		});

		item.addEventListener("mouseleave", function(){
			gsap.to(".custom-hover-circle, .custom-hover-text", {
				width: 0,
				height: 0,
				opacity: 0,
				duration: 0.3,
				ease: Power3.easeOut
			});
		});
	});
```
>.custom-hover 클래스를 가진 요소에 대해 mouseenter와 mouseleave 이벤트를
>추가하여 마우스가 해당 요소에 들어가거나 나갈 때의 동작을 정의합니다.
>mouseenter, mouseleave 이벤트에서 원과 텍스트가 나타나고 사라지고의 애니메이션을
>각각 지정해 부드러운 효과를 줍니다.

------------------------------------------------------


## 2. TOP 버튼 구현

> 화면의 위치에 따라 "TOP" 버튼이 동적으로 나타나고 사라지며, 버튼을 클릭하면 페이지의 최상단으로 부드럽게 스크롤 이동할 수 있는 기능을 구현하였습니다.

![Image](https://github.com/user-attachments/assets/65426bc8-1155-423c-a722-05005a2de5ba)  

![JavaScript](https://img.shields.io/badge/-JavaScript-dc8d2d?style=flat-square&logo=javascript&logoColor=ffffff)
```
	window.addEventListener("scroll", function(){
		let winH=window.innerHeight;

		if(window.scrollY > winH){
			if(!pageTop.classList.contains("show")){
				pageTop.classList.add("show");
			}
		}
		else{
			if(pageTop.classList.contains("show")){
				pageTop.classList.remove("show");
			}
		}
	});
```
>위 스크립트로 페이지를 스크롤할 때, 현재 스크롤 위치가 화면 높이보다 클 경우 pageTop 버튼이 표시됩니다.  
>반대로 스크롤 위치가 화면 높이 이하로 내려가면 버튼이 숨겨집니다.
```
	pageTop.addEventListener("click", function(){
		gsap.to(window, { scrollTo: 0, duration: 0.3, ease: Power3.easeOut });
	});
```
>pageTop 버튼을 클릭하면, 페이지가 부드럽게 최상단으로 스크롤됩니다. GSAP 라이브러리를 사용하여 애니메이션 효과를 추가합니다.









