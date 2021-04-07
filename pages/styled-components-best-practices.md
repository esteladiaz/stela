# Best practices with Styled Components

Say we have a component and it takes props for opacity and color. How to you apply the properties to the `<Wrapper />`?
1. Interpolation function: ass a function to the styled-component's template literal, adapt it based on its props.

```js
function Backdrop({ opacity, color, children }) {
  return (
    <Wrapper opacity={opacity} color={color}>
      {children}
    </Wrapper>
  )
}

const Wrapper = styled.div`
  opacity: ${p => p.opacity};
  background-color: ${p => p.color};
`;
```
Everytime values change, styled-components needs to regenerate the classes and re-inject them into the document `<head>`. This can be a performance liability (like JS animations)

Solve the problem with CSS variables: 
```js
function Backdrop({ opacity, color, children }) {
  return (
    <Wrapper
      style={{
        '--color': color,
        '--opacity': opacity,
      }}
    >
      {children}
    </Wrapper>
  )
}

const Wrapper = styled.div`
  opacity: var(--opacity);
  background-color: var(--color);
`;
```


CSS variables let you animate any property because you're not applying the transition to the proprty, you're aplying it to the value

