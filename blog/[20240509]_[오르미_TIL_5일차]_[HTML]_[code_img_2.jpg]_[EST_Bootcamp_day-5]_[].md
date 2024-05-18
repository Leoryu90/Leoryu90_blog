## 오르미 백엔드 5일차

#### HTML 표(table)

- 테이블을 생성한다.

테이블 기본 형식
```html
<table>
    <caption>표에대한 설명</caption>
    <thead></thead>
    <tbody>
        <tr>
            <th></th> or <td></td>
        </tr>
    </tbody>
    <tfoot></tfoot>
</table>
```
표(table)을 이해할 수 있는 예시

![표(table)을 이해할 수 있는 예시](img/day5/table.png)


#### tr, th, td
- **tr**: table row. 테이블의 행
- **th**: table header. 테이블의 행, 열의 제목을 나타내는 셀
- **td**: table data. 셀 내용

#### caption
- 테이블의 제목이나 설명을 쓰는 태그입니다.

#### thead, tbody, tfoot
- **thead**: 테이블 행 블록(row block) 내에 **제목 열 그룹**(column headers)으로 구성할 경우 사용.
- **tbody**: 행 블록 내에 **테이블 데이터**로 구성할 때 사용.
- **tfoot**: 행 블록 내에 **열 요약**(column summaries)로 구성할 때 사용.

#### colspan, rowspan

- colspan: 열 병합
- rowspan: 행 병합

> **주의사항**:\
> 열별합은 열과 열의 병합으로 우리가 생각할 때에는 행병합입니다.\
> 행 병합도 같은 방식의 작용을 가집니다.

#### col, colgroup

- **colgroup**: 테이블 열 그룹을 만들고 싶을 때 사용합니다
- **col**: 테이블 열을 하나 이상 묶을 때 사용, colgroup 요소 내부에 포함.(필수X)

예시
```html
<table>
    <colgroup>
        <col> 
        <col span="2" class="batman">
        <col span="2" class="flash">
    </colgroup>
</table>
```

-------------------
