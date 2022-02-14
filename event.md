# 이벤트

## 💁‍♂️ 질문 목록

```txt
Q1. 이벤트 캡처링에 대해서 설명해주세요.
Q2. 이벤트 버블링에 대해서 설명해주세요.
Q3. 이벤트 위임이란 무엇인가요?
Q4. 이벤트 위임의 장점은 무엇인가요?
Q5. 자바스크립에서 보통 어떤 식으로 이벤트를 설계해야 하나요?
```

## 💁‍♀️ 답변 목록

<details>
<summary><strong>Q1. 이벤트 캡처링에 대해서 설명해주세요.</strong></summary>

(what) 이벤트 캡처링이란 이벤트 전파의 첫 번째 단계로 상위 요소에서 이벤트 타겟 요소로 이벤트가 전파되는 과정을 말합니다. (how) 캡처링 단계로 이벤트를 잡아내려면 addEventListener에 세번째 인자에 true를 넣어주면 됩니다.

</details>

<details>
<summary><strong>Q2. 이벤트 버블링에 대해서 설명해주세요.</strong></summary>

(what) 이벤트 버블링이란 이벤트 전파의 세 번째 단계로 이벤트 타겟 요소에서 상위 요소로 이벤트가 전파되는 과정을 말합니다. (how) 만약 이벤트 타겟 요소의 상위 요소에도 동일한 이벤트에 대한 핸들러가 등록되어 있으면 이벤트 버블링으로 인해 부모 요소의 모든 이벤트 핸들러도 실행되기 때문에 이를 막기 위해서는 event.stopPropagation 메서드를 사용할 수 있습니다.

</details>

<details>
<summary><strong>Q3. 이벤트 위임이란 무엇인가요?</strong></summary>

(what) 이벤트 위임은 이벤트 핸들링 패턴으로, 비슷한 방식으로 여러 요소에 동일한 핸들러를 등록해야 할 때 요소의 공통 조상에 이벤트 핸들러를 단 하나만 등록해서 여러 요소를 한꺼번에 다루는 방법입니다. (how) 공통 조상에 할당한 핸들러에서 event.target 속성을 이용하면 실제 이벤트가 어디서 발생했는지 알 수 있으므로 중복 코드 없이 개별적인 이벤트 핸들링을 쉽게 할 수 있습니다.

</details>

<details>
<summary><strong>Q4. 이벤트 위임의 장점은 무엇인가요?</strong></summary>

(what) 중복 코드를 작성하지 않고도 여러 요소에 대해 한 번에 이벤트를 핸들링할 수 있고, 코드가 적어지므로 유지 보수에도 용이하며, 동적으로 하위 DOM요소를 추가해야할 경우 일일이 이벤트 핸들러를 등록하지 않아도 됩니다. 또한 여러 요소에 이벤트를 등록하지 않아도 되므로 성능 저하도 막을 수 있습니다.

</details>

<details>
<summary><strong>Q5. 자바스크립에서 보통 어떤 식으로 이벤트를 설계해야 하나요?</strong></summary>

(how) 여러 요소에 동일한 이벤트 핸들링을 할 때는 개별 요소에 모두 이벤트 핸들러를 등록하기보다는 이벤트 위임 패턴을 사용하는 것이 더 좋습니다. (why) 왜냐하면 중복 코드를 작성하지 않고도 여러 요소에 대해 한 번에 이벤트를 핸들링할 수 있고, 코드가 적어지므로 유지 보수에도 용이하며, 동적으로 하위 DOM요소를 추가해야할 경우 일일이 이벤트 핸들러를 등록하지 않아도 됩니다. 또한 여러 요소에 이벤트를 등록하지 않아도 되므로 성능 저하도 막을 수 있습니다.

(how) document 요소에 이벤트 핸들러를 등록할 때는 프로퍼티 방식보다는 addEventListener를 사용하는 것이 좋습니다. (why) 왜냐하면 프로퍼터 방식으로 등록하면 이전에 등록된 핸들러를 새로 덮어씌우지만, addEventListener방식은 기존 이벤트 핸들러를 유지하면서 새롭게 추가하기 때문입니다.

</details>

## 💁 추가질문

<details>
<summary><strong>Q. event.target vs event.currentTarget? </strong></summary>

- event.target: 이벤트가 발생한 요소
- event.currentTarget: 이벤트 핸들러를 등록한 요소

```html
<table>
  <tr>
    <th colspan="3">
      <em>Bagua</em> Chart: Direction, Element, Color, Meaning
    </th>
  </tr>
  <tr>
    <td class="nw">
      <strong>Northwest</strong><br />Metal<br />Silver<br />Elders
    </td>
    <td class="n">...</td>
    <td class="ne">...</td>
  </tr>
  <tr>
    ...2 more lines of this kind...
  </tr>
  <tr>
    ...2 more lines of this kind...
  </tr>
</table>

<script>
  table.onclick = function (event) {
    let td = event.target.closest("td"); // (1)

    if (!td) return; // (2)

    if (!table.contains(td)) return; // (3)

    highlight(td); // (4)
  };
</script>
```

위 코드에서 td를 클릭했을 때

- `event.target`: td
- `event.currentTarget`: table

</details>

## 📚 함께 읽기

- [버블링과 캡처링](https://ko.javascript.info/bubbling-and-capturing#ref-2412)
- [이벤트 위임](https://ko.javascript.info/event-delegation)
