A syntax extension that lets you write HTML-like code inside JavaScript.
```
const App = () => <h1>Hello, React!</h1>;
```
### rules for jsx
- we can enter in js mode using curly braces.
- statements are not allowed like (if/else, for, switch) but we can write them outside jsx.
- a piece of jsx can only return one root element if you want more than one then you have to use react.fragments.
- use className instead of just class
- every tag needs to be closed like <br />
- everything should be in camel case which are originally in kebab case.
- exception aria-* and data-* are written with dashes like in HTML.
- css inline styles are written like this: {{..}}
- comments are also need to be in { } as they are in js.