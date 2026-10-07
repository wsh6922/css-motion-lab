### Learned

- `place-content: center`는 해당 요소의 **직속 자식까지만 정렬**한다.
- 부모가 가운데 정렬되어도, 그 안쪽 자식들은 자기 부모 안에서 다시 기본 문서 흐름을 따른다.
- 손자 요소까지 가운데 오게 하려면 그 손자의 부모에도 별도로 정렬을 줘야 한다.

```css
.container {
  display: grid;
  place-content: center;
}
```

```html
<div class="container">
  <div class="box">
    <div class="box_paper">
      <div class="box_text">A</div>
    </div>
  </div>
</div>
```

```text
.container → .box까지만 가운데 정렬
.box → .box_paper는 따로 배치해야 함
.box_paper → .box_text는 따로 배치해야 함
```

---

- `position: absolute`만 주면 요소가 부모 전체를 자동으로 덮지 않는다.
- `top`, `left`, `right`, `bottom`, `width`, `height`, `inset` 같은 위치/크기 조건이 없으면 내용 크기만큼 잡힐 수 있다.
- 그래서 `.box_paper` 안에 `A`만 있으면 배경도 `A` 콘텐츠 크기만큼만 보인다.
- 부모 `.box` 전체를 덮고 싶으면 `inset: 0`을 줘야 한다.

```css
.box {
  position: relative;
}

.box_paper {
  position: absolute;
  inset: 0;
}
```

---

```text
화면
└─ container
   └─ box
      └─ ::after
```

```text
      요구사항
        ↓
"박스가 굴렀으면 좋겠다."
        ↓
굴러가려면 어디를 축으로 돌지?
        ↓
오른쪽 아래 모서리
        ↓
transform-origin: right bottom
        ↓
처음에는?
0°
        ↓
넘어진 순간에는?
90°
        ↓
그 다음 칸으로 이동
translateX(100%)
        ↓
착지하면서 살짝 흔들리게
rotate(8deg)
        ↓
다시 똑바로
rotate(0deg)
```
