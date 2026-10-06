### Learned

- `place-content: center`는 해당 요소의 직속 자식까지만 정렬한다.
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

```txt
.container → .box까지만 가운데 정렬
.box → .box_paper는 따로 배치해야 함
.box_paper → .box_text는 따로 배치해야 함
```

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
