# React源码分析

## React之JSX的实现

```jsx
function Comp(){
    return (
        <div>Comp</div>  
    )
}

<Comp id="div" key="key">
    <span>1</span>
    <span>1</span>
</Comp>    
```

{% hint style="info" %}
转换成ES5 
{% endhint %}

```jsx
"use strict";
    
// 组件必须为大写，如果为小写，react会认为这个标签为原生的html标签
function Comp() {
    return React.createElement("div", null, "Comp");
}

React.createElement(
    Comp, // 若为小写，react会认为是原声html标签，此时会解析为字符串，
    {
        id: "div",
        key: "key"
    },
    React.createElement("span", null, "1"),
    React.createElement("span", null, "1")
);    
```

