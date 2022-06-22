

# [jQuery] 효과



### jQuery 효과

- Basic 효과
  - ``hide() / show() / toggle()``
- Sliding 효과
  - ``slideDown() / slideUp() / slideToggle()``
- Fading 효과
  - ``fadeIn() / fadeOut() / fadeToggle() / fadeTo()``
- Animate 효과
  - ``Animate(속성)``



#### Basic 효과

```
hide() 
: 요소 숨기기

show() 
: 요소 표시

toggle() 
: 요소를 숨기거나 표시, show() / hide() 교대로 실행
```



#### 공통 인수

- duration : 효과 진행 속도 (slow / normal /fast )
- Callback(function()) : 효과 완료 후 수행할 함수
- ``easing``
  - 전체 애니메이션의 적용 시간 비율을 원하는 진행 비율로 매핑
  - ``swing``
    - 사인 곡성(느리게 시작해서 빠르게 진행되다가 나중에 다시 느려지는 효과)
  - ``linear`` : 선형 (일정한 속도로 진행)

```
// toggle3 버튼 - 속도 3초 / 진행 : linear
$('#toggle3').on('click',function(){
	$('img').toggle(3000, 'linear');
});
```



#### Sliding 효과

- ``slidDown()`` : 요소를 슬라이딩 효과로 나타나게 함

- ``slideUp()`` : 요소를 슬라이딩 효과로 숨김
- ``slideToggle()`` : 슬라이딩 해서 숨겼다 보였다 교대로 실행
  - ``slideDown() / slideUp()`` 교대로 실행

- [메뉴]에 마우스 올리면 subMenuBox가 slideDown 되면서, 영역 나나타고 이미지 보임
- 마우스 떼면 slideUp 되면서 영역도 사라지고 이미지도 안 보임



***슬라이딩 효과 주의!***

- 슬라이딩 효과는 <div> 박스에 적용
- 이미지에 슬라이딩 효과를 주면 전체적으로 축소/확대되면서 사라졌다가 보여짐



***참고***

- ``display:none; ``
  - 보이지 않고  차지하고 있는 영역 없음
- ``visibility:hidden; ``
  - 보이지 않지만 차지하고 있는 영역은 있음



#### Fading 효과

- ``fadeIn()`` : 요소를 선명하게 만들면서 나타남
- ``fadeOut()`` : 요소를 흐리게 하면서 숨김 (영역도 사라짐)
- ``fadeToggle() : fadeIn() / fadeOut()`` 교대로 실행
- ``fadeTo()``
  - 요소의 불투명도 조정
  - 투명도 0으로 안 보여도 영역은 그대로 남아 있음



#### Animate 효과

- animate(속성)
  - 사용자  CSS 효과를 지정하여 애니메이션 수행

- animate() 형식1

<img width="400" alt="image-20220623000147487" src="https://user-images.githubusercontent.com/101630615/175063567-1169f803-9c32-46bc-bd01-5f6d42ee5a5f.png">

- animate() 형식2

<img width="400" alt="image-20220623000156836" src="https://user-images.githubusercontent.com/101630615/175063581-c61f09a8-0bdf-4b11-b53a-6147df9e130f.png">



#### 애니메이션 정지

- ``$(선택자).stop();``  // false 입력한 것으로 간주
- ``$(선택자).stop(true);``  // clearQueue수행
- ``$(선택자).stop(true, true); ``
- ``clearQueue, goToEnd`` 수행



#### ``clearQueue``

- 대기열에 있는 함수 모두 제거
- 예약된 애니메이션 초기화 
- ``clearQueue()`` 메소드 실행 효과

#### ``goToEnd``

- 제자리에서 멈추는 것이 아니라 지정한 최종 형태에서 멈춤 
- (애니메이션 진행 중간에 멈추는 것이 아니라 마지막까지 수행되고 멈춤)

