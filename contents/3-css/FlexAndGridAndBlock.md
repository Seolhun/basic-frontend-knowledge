# CSS, Grid, Flex And Block

## Grid

#### - grid-gap
`grid-gap`은 row와 columns의 간격의 크기를 정의하는 속성입니다. `grid-row-gap`과 `grid-column-gap`의 두가지 하위 속성이 있습니다.

grid-gap은 row, column 순으로 px을 지정할 수 있으며, row와 column 별로 지정할 수 있습니다. 간단히 아래처럼 사용하세요.
```scss
.grid-gap {
	grid-gap: 10px;
	grid-gap: 10px 5px;
	grid-row-gap: 10px;
	grid-column-gap: 5px;
}
```

#### - grid-template-areas
`grid-template-areas`는 grid layout 안에서 영역을 지정하는 속성입니다.

`grid-area` 속성을 사용하여 grid 항목의 이름을 지정한 다음, grid-template-areas 속성의 이름을 참조시킬 수도 있습니다.

```scss
.grid-container {
  display: grid;
  grid-template-areas:
    'header header header '
    'left center right'
    'footer footer footer ';
  grid-gap: 5px;
}
```

## Flex


## Block


## Practices
#### Part 1 - Grid
<script async src="//jsfiddle.net/SHun10114/637hy0bp/embed/html,css,result/"></script>


#### Part 2 - Flex
<script async src="//jsfiddle.net/SHun10114/y28uf5d3/embed/html,css,result/"></script>


#### Part 3 - Block
<script async src="//jsfiddle.net/SHun10114/L4epjq26/embed/html,css,result/"></script>
