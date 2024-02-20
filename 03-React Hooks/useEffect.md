# 정의

useEffect는 컴포넌트 내 여러 값을 활용해 동기적으로 부수효과를 만들기 위해 사용하는 매커니즘이다.

# 형태

```jsx
useEffect(() => {}, []);
```

첫번째 인수에 있는 함수: 부수 효과
두번째 인수에 있는 배열: 부수 효과를 일으키는 조건

# useEffect 동작 원리

선행 개념: 함수형 컴포넌트는 매번 함수를 실행하여 렌더링을 수행한다. 렌더링 시마다 고유의 state와 props를 갖고 있다.
useEffect는 이러한 함수형 컴포넌트의 렌더링 과정에서 두 번째 인수에 있는 의존성 값이 달라지면 렌더링된다. 다시 말해 useEffect는 함수형 컴포넌트의 렌더링 특성에 따른 부수 효과이다.

이때 의존성 배열 비교는 이전 값과 현재 값의 얕은 비교라는 점이 핵심이다.

# useEffect 유무에 따른 렌더링 차이

```jsx
function Component() {
  console.log("렌더링됨");
}

function UseEffectComponent() {
  useEffect(() => {
    console.log("렌더링됨");
  }, []);
}
```

useEffect는 CSR을 보장하기 때문에 useEffect 내부에서 window 객체 접근에 의존하는 코드를 사용할 수 있다.

# useEffect 사용 시 주의사항
