## 오르미 백엔드 5일차

### 💡 HTML 표(table)

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
- `tr`: table row. 테이블의 행
- `th`: table header. 테이블의 행, 열의 제목을 나타내는 셀
- `td`: table data. 셀 내용