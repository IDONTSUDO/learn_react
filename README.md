## React Component Fn

есть 2 вида записи функциональных реакт компонентов

```typescript
export const Foo = () => <></>;
```

```typescript
export function Foo() {
  return <></>;
}
```

необходимые условия

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
export const Foo = (props) => (<>{props.bar}</>)

<Foo bar={"123"}/>
```

второй пример как можно указать пропсы.

```typescript
interface IFooProps{
    bar:string;
}
export const Foo = ({bar}) => (<>{bar}</>)

<Foo bar={"123"}/>
```
