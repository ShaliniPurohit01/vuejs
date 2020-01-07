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

- correct method is to use **v-bind** which will bind dynaic content of the attributes

```html
<div id="vue-div">
  <h2>Data binding</h2>
  <a v-bind:href="website"></a>
  <!-- or -->
  <a :href="website"></a>
  <!-- or -->
  <input type="text" v-bind:value="name" />
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

- if we put functions into method, then if we click one of the button, both the button will work
- if we put the functions in computed field, then only that button will work which was clicked

```html
<div>
  <button v-on:click="a++">add to A</button>
  <button v-on:click="b++">add to B</button>
  <p>Age + A ={{addToA}}</p>
  <p>Age + B ={{addToB}}</p>
</div>
```

```js
new Vue({
  el: "#vue-div",
  data: {
    age: 20,
    a:0,
    b:0
  },
  computed:{
    addToA:function{
      return this.a +this.age;
    },
    addToB:function{
      return this.b +this.age;
    }
  }
});
```

# dynamic CSS

- normal css

```html
<div>
  <div v-bind:class="{ red:true, blue:false }"></div>
  <!-- red will become its class-->
</div>
```

- dynamic

```html
<div>
  <div v-on:click="available = !available" v-bind:class="{available}">
    <span>shaily</span>
  </div>
</div>
```

```js
new Vue({
  el: "#vue-div",
  data: {
    available: false
  },
  method: {},
  computed: {}
});
```

- other example

```html
<div>
  <button v-on:click="nearby = !nearby">toggle nearby</button>
  <button v-on:click="available = !available">toggle available</button>
  <div v-bind:class="compClasses">
    <span>Shaily</span>
  </div>
</div>
```

```js
new Vue({
  el: "#vue-div",
  data: {
    available: false,
    nearby:false
  },
  method: {},
  computed: {
    compClasses:function{
      return{
        available:this.available,
        nearby:this.nearby
      }
    }
  }
});
```

# conditionals

- v-if and v-show
- v-if and v-show works same the only diffrence is that v-show will set display property to none if the value is false
- if will not take that object from dome

```html
<div>
  <button v-on:click="error = !error">Error</button>
  <button v-on:click="success=!success">Success</button>
  <p v-if="error">There has been an error</p>
  <p v-if="success">!!! Success !!!</p>

  <!-- OR -->
  <p v-if="error">There has been an error</p>
  <p v-else-if="success">!!! Success !!!</p>

  <!-- Or -->
  <p v-show="error">There has been an error</p>
  <p v-show="success">!!! Success !!!</p>
</div>
```

```js
new Vue({
  el: "#vue-div",
  data: {
    error: false,
    success: false
  },
  method: {},
  computed: {}
});
```

# looping

```html
<div>
  <ul>
    <li v-for="c in characters">{{c}}</li>
    <li v-for="n in ninjas">{{n.name}}- {{n.age}}</li>
    <!-- show with index  value-->
    <li v-for="(n, index) in ninjas">{{index}}.{{n.name}}- {{n.age}}</li>
  </ul>

  <!-- loop through objects -->
  <template v-for="n nn ninjas">
    <div v-for="(val,key) in ninjas">
      <p>
        {{key}} - {{val}}
      </p>
    </div>
  </template>
</div>
```

```js
new Vue({
  el: "#vue-div",
  data: {
    characters: ["Mario", "Lugi", "Yoshi"],
    ninjas: [
      { name: "shaily", age: 23 },
      { name: "Jay", age: 18 },
      { name: "xyz", age: 20 }
    ]
  },
  method: {},
  computed: {}
});
```

## multiple vue instances

```html
<div>
  <div id="vue-div-one">
    <h1>{{title}}</h1>
    <p>{{greet}}</p>
  </div>

  <div id="vue-div-two">
    <h1>{{title}}</h1>
    <p>{{greet}}</p>
  </div>
</div>
```

```js
var one = new Vue({
  el: "#vue-div-one",
  data: {
    title: "vue app one"
  },
  method: {},
  computed: {
    greet:function{
      return "hello from vue one";
    }
  }
});

var two = new Vue({
  el: "#vue-div-two",
  data: {
    title: "vue app two"
  },
  method: {},
  computed: {
    greet:function{
      return "hello from vue 2";
    }
  }
});
```

- communicating between 2 vue instances

```html
<div>
  <div id="vue-div-one">
    <h1>{{title}}</h1>
  </div>

  <div id="vue-div-two">
    <h1>{{title}}</h1>
    <button v-on:click="changeTitle">A change on app one title</button>
  </div>
</div>
```

```js
var one = new Vue({
  el: "#vue-div-one",
  data: {
    title: "vue app one"
  },
  method: {},
  computed: {}
});

var two = new Vue({
  el: "#vue-div-two",
  data: {
    title: "vue app two"
  },
  method: {
    changeTitle: function() {
      one.title = "title changes for one";
    }
  },
  computed: {}
});
two.title = "title changes from outside for two";
```

# Components

```html
<div>
  <div id="vue-div-one">
    <greeting> </greeting>
  </div>

  <div id="vue-div-two">
    <greeting> </greeting>
  </div>
</div>
```

```js
Vue.component('greeting',{
  template:'<p> Hey.. {{name}}. <button v-on:click="changeName">Change Name</button></p>',
  data:function(){
    return{
      name:'shaily'
    }
  },
  method: {
    changeName:function(){
      this.name='mario';
    }
  }

  }
})
new Vue({
  el: "#vue-div-one",
  data: {},
  method: {},
  computed: {}
});

new Vue({
  el: "#vue-div-two",
  data: {
  },
  method: { },
  computed: {}
});
```

- OR

```js
var data={
  name:'Yoshi'
}
Vue.component('greeting',{
  template:'<p> Hey.. {{name}}. <button v-on:click="changeName">Change Name</button></p>',
  data:function(){
    return data
    },
  method: {
    changeName:function(){
      this.name='mario';
    }
  }

  }
})
new Vue({
  el: "#vue-div-one",
  data: {},
  method: {},
  computed: {}
});

new Vue({
  el: "#vue-div-two",
  data: {
  },
  method: {

    }
  },
  computed: {}
});
```

# Reference using \$ref

```js
new Vue({
  el: "#vue-div-one",
  data: {
    output: "your fav food"
  },
  method: {
    readRefs: function() {
      console.log(this.$refs.input.value);
      this.output = this.$refs.input.value;
    }
  },
  computed: {}
});
```

```html
<div>
  <div id="vue-div-one">
    <h2>Refs</h2>
    <input type="text" ref="input" />
    <button v-on:click="readRefs">Submit</button>
    <p>Your fav food : {{output}}</p>
  </div>
</div>
```
