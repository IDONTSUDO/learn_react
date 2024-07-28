## JSX/TSX/DOM/HTML

JSX/TSX === HTML/DOM является полностью эквивалентными элементами все что работает в HTML,DOM сработает в JSX/TSX

Отсутсвие HTML тэга в JSX/TSX.

```typescript
<></>
```

Единый тэг.

```tsx
<div />
```

Двойной тэг.

```tsx
<div></div>
```

### Обработка основных событий

События в HTML
https://learn.javascript.ru/introduction-browser-events

```tsx
<>
<div onClick=(() => fn())/>
<div onChange=(() => fn())/>
</>

```

## Функциональные React Component

есть 2 вида записи функциональных реакт компонентов

```typescript
export const Foo = () => <></>;
```

```typescript
export function Foo() {
  return <></>;
}
```

необходимые условия !

- React компоненты должны быть названы с большой буквы.
- React компоненты должны возвращать JSX/TSX.

2 способа вызова компонента.

```
<Foo/>
<Foo></Foo>
```

## JSX/TSX -> TS/JS

Для того что бы в JSX/TSX вставить JS/TS используются фигурные скобки {}

##### Пример вставки разных типов.

String -> {""}

Number -> {1}

undefined -> {undefined}

null -> {null}

bollean -> {true}

Array -> {[1,2,3].map((el) => <>{el}</>)}

Object {{}}

необходимые условия

- Мы не можем использовать функции которые возвращают void/undefined. Примером таких функций является console.log() .forEach()

### React Component Props

Пропсы у комопнентов служат для предачи данных между компонентами.

минимальный пример указания пропсов.

```typescript
interface IFooProps{
    bar:string;
}
export const Foo = (props:IFooProps) => (<>{props.bar}</>)

<Foo bar={"123"}/>
```

второй пример как можно указать пропсы.

```typescript
interface IFooProps{
    bar:string;
}
export const Foo = ({bar}:IFooProps) => (<>{bar}</>)

<Foo bar={"123"}/>
```

Опциональные пропсы. С добавлением после объявления свойства добавляется ? что означает что свойство может быть undefined и оно является не обязательным.

```typescript
interface IFooProps{
    bar:string;
    biz?:string;
}
export const Foo = ({bar}:IFooProps) => (<>{bar}</>)

<Foo bar={"123"}/>
```

Пропсы для передачи стилей

```typescript
interface IFooProps{
    style:React.CSSProperties;
    biz?:string;
}
export const Foo = ({bar}:IFooProps) => (<div style={props.style}>{bar}</div>)

<Foo style={{color:"red"}}/>
```

Пропсы для передачи React компонента.

```typescript
interface IFooProps{
    child:React.ReactNode;
}
export const Foo = ({child}:IFooProps) => (<div>{child}</div>)

<Foo child={<>ТУТ JSX</>}/>
<Foo child={<Foo child={<>ТУТ JSX</>}/>}/>

```

React Router

### Установка

npm i react-router-dom

### Применение

```typescript
import ReactDOM from "react-dom/client";
import { RouterProvider, useNavigate } from "react-router-dom";
import { createBrowserRouter } from "react-router-dom";
//путь до экрана записанный в переменной
export const BarScreenPath = "/bar";
export const BarScreen = () => {
    //Использование хука useNavigate для получения функции переключения экранов
  const navigate = useNavigate();

  return (
    <div
      onClick={() => {
        navigate(FooScreenPath);
      }}
    >
      Bar
    </div>
  );
};

export const FooScreenPath = "/foo";
export const FooScreen = () => {
  const navigate = useNavigate();

  return (
    <div
      onClick={() => {
        navigate(BarScreenPath);
      }}
    >
      FOO
    </div>
  );
};

const root = ReactDOM.createRoot(document.getElementById("root") as HTMLElement);

export const router = createBrowserRouter([
  {
    path: FooScreenPath,
    element: <FooScreen />,
  },
  {
    path: BarScreenPath,
    element: <BarScreen />,
  },
]);
root.render(
  <>
    <RouterProvider router={router} />
  </>
);

```
