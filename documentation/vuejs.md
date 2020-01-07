## vue js

- frontend framework
- no need to make multiple server request for page

## why?

1. very lean
2. very high run time performance

## Vue Instance

```js
new Vue({
  //control whole/several path of the application
  el: "#vue-div", // define which ele in vue are going to control the application
  //root element
  data: {
    //it will hold actual data, in key-value pairs
    name: "shaily"
  }
});
```

```html
<div id="vue-div">
  <h1>{{name}}</h1>
</div>
```

## data and methods

```js
new Vue({
  el: "#vue-div",
  data: {
    name: "shaily"
  },
  method: {
    greet: function() {
      return "hey!";
    }
  }
});
```

```html
<div id="vue-div">
  <h2>{{greet()}}</h2>
  <p>{{name}}</p>
</div>
```

- with parameter

```js
new Vue({
  el: "#vue-div",
  data: {
    name: "shaily"
  },
  method: {
    greet: function(time) {
      return "Good" + time;
    }
  }
});
```

```html
<div id="vue-div">
  <h2>{{greet('Afternoon')}}</h2>
  <p>{{name}}</p>
</div>
```

- access data inside vue instance

```js
new Vue({
  el: "#vue-div",
  data: {
    name: "shaily"
  },
  method: {
    greet: function() {
      return "Good" + time + this.name;
    }
  }
});
```

## data binding

**_v-bind_**

```js
new Vue({
  el: "#vue-div",
  data: {
    name: "shaily",
    website:"https://www.youtube.com/"
  },
  method: {

    }
  }
});
```

```html
<div id="vue-div">
  <h2>Data binding</h2>
  <a href="website"></a>
  <a href="{{website}}"></a>
  <a href="{{website}}"></a>
  <!-- nothing will work here -->
</div>
```

- correct method is to use **\*v-bind** which will bind dynaic content of the attributes

```html
<div id="vue-div">
  <h2>Data binding</h2>
  <a v-bind:href="website"></a>
  <!-- or -->
  <a :href="website"></a>
  <!-- or -->
  <input type="text" v-bind:value="name" />
  >
</div>
```

**_v-html_**

- used to bind direct html tags

```js
new Vue({
  el: "#vue-div",
  data: {
    name: "shaily",
    websiteTag:'<a href="https://www.youtube.com/">Click to open YouTube</a>'
  },
  method: {

    }
  }
});
```

```html
<div id="vue-div">
  <p v-html="websiteTag"></p>
</div>
```

## Events

- v-on: directive is used for handling mouse events
- @click

```html
<button v-on:click="age++">add</button>
<p>{{age}}</p>
```

- or we can use methods without ()

```js
new Vue({
  el: "#vue-div",
  data:{
    age:25
  },
  method: {
      add:function(){
        this.age++;
      }
    }
  }
});
```

```html
<button v-on:click="add">add</button>
<p>{{age}}</p>
```

- doubleclick event
- v-on:dblclick
- @dblclick

- v-on:mousemove

```js
new Vue({
  el: "#vue-div",
  data:{
    age:25
  },
  method: {
    update:function(event){
        this.x=event.offsetX;
      }
    }
  }
});
```

```html
<div v-on:mousemove="update">{{x}}</div>
```

## event modifiers

- once
- stop
- prevent
- capture
- self

```html
<button v-on:click.once="age++">add</button>
<p>{{age}}</p>
```

# keyboard events

- keydown
- keypress
- keyup
- with modifiers like
- .enter
- .tab
- .delte
- .esc
- .up
- .down
- .left
- .right etc

```html
<input type="text" v-on:keyup.enter="logName" />
<input type="text" v-on:keyup.alt.enter="logAge" />
```

# 2 way data binding

- v-model

```html
<input type="text" v-madel="name" />
<span>{{name}}</span>
<input type="text" v-model="age" />
<span>{{age}}</span>
```

```js
new Vue({
  el: "#vue-div",
  data: {
    name: "",
    age: ""
  }
});
```

# computed properties
