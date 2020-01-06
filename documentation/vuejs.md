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
<>
