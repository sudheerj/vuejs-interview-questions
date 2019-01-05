# vuejs-interview-questions
List of 300 VueJS Interview Questions

> Click :star:if you like the project. Pull Request are highly appreciated.

### Table of Contents
-------------------------------------------------------------------
| No. | Questions |
|---- | ---------
|1  | [What is VueJS](#what-is-vuejs) |
|2  | [What are the major features of VueJS](#what-are-the-major-features-of-vuejs) |
|3  | [What are the lifecycle methods of VueJS](#what-are-the-lifecycle-methods-of-vuejs)|
|4  | [What are the conditional directives](#what-are-the-conditional-directives)|
|5  | [What is the difference between v-show and v-if directives](#what-is-the-difference-between-v-show-and-v-if-directives)|
|6  | [What is the purpose of v-for directive?](#what-is-the-purpose-of-v-for-directive)|
|7  | [What is vue instance?](#what-is-vue-instance)|
|8  | [How do you achieve conditional group of elements?](#how-do-you-achieve-conditional-group-of-elements)|
|9  | [How do you reuse elements with key attribute?](#how-do-you-reuse-elements-with-key-attribute)|
|10 | [Why should not use if and for directives together on the same element?](#why-should-not-use-if-and-for-directives-together-on-the-same-element)|
|11 | [Why do you need to use key attribute on for directive?](#why-do-you-need-to-use-key-attribute-on-for-directive)|
|12 | [What are the array detection mutation methods?](#what-are-the-array-detection-mutation-methods)|
|13 | [What are the array detection non mutation methods?](#what-are-the-array-detection-non-mutation-methods)|
|14 | [What are the caveats of array changes detection?](#what-are-the-caveats-of-array-changes-detection)|
|15 | [What are the caveats of object changes detection?](#what-are-the-caveats-of-object-changes-detection)|
|16 | [How do you use for directive with a range?](#how-do-you-use-for-directive-with-a-range)|
|17 | [How do you use for directive on template?](#how-do-you-use-for-directive-on-template)|
|18 | [How do you use event handlers?](#how-do-you-use-event-handlers)|
|19 | [What are the event modifiers provided by vue?](#what-are-the-event-modifiers-provided-by-vue)|
|20 | [What are key modifiers?](#what-are-key-modifiers)|
|21 | [How do you define custom key modifier aliases?](#how-do-you-define-custom-key-modifier-aliases)|
|22 | [What are the supported System Modifier Keys?](#what-are-the-supported-system-modifier-keys)|
|23 | [What are the supported Mouse Button Modifiers?](#what-are-the-supported-mouse-button-modifiers)|
|24 | [How do you implement two way binding?](#how-do-you-implement-two-way-binding)|
|25 | [What are the supported modifiers on model?](#what-are-the-supported-modifiers-on-model)|
|26 | [What are components and give an example?](#what-are-components-and-give-an-example)|

1.  ### What is VueJS?
    Vue.js is an open-source, progressive Javascript framework for building user interfaces that aim to be incrementally adoptable. The core library of VueJS is focused on the view layer only, and is easy to pick up and integrate with other libraries or existing projects.
2.  ### What are the major features of VueJS?
    Below are the some of major features available with VueJS
    1. **Virtual DOM:** It uses virtual DOM similar to other existing frameworks such as ReactJS, Ember etc. Virtual DOM is a light-weight in-memory tree representation of the original HTML DOM and updated without affecting the original DOM.
    2. **Components:** Used to create reusable custom elements in VueJS applications.
    3. **Templates:** VueJS provides HTML based templates that bind the DOM with the Vue instance data
    4. **Routing:** Navigation between pages is achieved through vue-router
    5. **Light weight:** VueJS is light weight library compared to other frameworks
3.  ### What are the lifecycle methods of VueJS?
4.  ### What are the conditional directives?
    VueJS provides set of directives to show or hide elements based on conditions. The available directives are: ** v-if, v-else, v-else-if and v-show**
    **1. v-if:**  The v-if directive adds or removes DOM elements based on the given expression. For example, the below button will not show if isLoggedIn is set to false.
    ```javascript
    <button v-if="isLoggedIn">Logout</button>
    ```
    You can also control multiple elements with a single v-if statement by wrapping all the elements in a <template> element with the condition. For example, you can have both label and button together conditionally applied,
    ```javascript
    <template v-if="isLoggedIn">
      <label> Logout </button>
      <button> Logout </button>
    </template>
    ```
    **2. v-else:**  This directive is used to display content only when the expression adjacent v-if resolves to false. This is similar to else block in any programming language to display alternative content and it is preceded by v-if or v-else-if block. You don't need to pass any value to this.
    For example, v-else is used to display LogIn button if isLoggedIn(not logged in) is set to false.
    ```javascript
    <button v-if="isLoggedIn"> Logout </button>
    <button v-else> Log In </button>
    ```
    **3. v-else-f:** This directive is used when we need more than two options to be checked.
    For example, ifLoginDisabled property is disabled then we need to prevent user to login instead just display the label. This can be achieved through v-else statement.
    ```javascript
    <button v-if="isLoggedIn"> Logout </button>
    <label v-else-if="isLoginDisabled"> User login disabled </label>
    <button v-else> Log In </button>
    ```

    **4. v-show:** This directive is similar to v-if but it renders all elements to the DOM and then uses the CSS display property to show/hide elements. This directive is recommended if the elements are switched on and off frequently.
    ```javascript
    <span if-show="user.name">Welcome user,{{user.name}}</span>
    ```
5.  ### What is the difference between v-show and v-if directives?
    Below are some of the main differences between between **v-show** and **v-if** directives,
        1. v-if only renders the element to the DOM if the expression passes whereas v-show renders all elements to the DOM and then uses the CSS display property to show/hide elements based on expression.
        2. v-if supports v-else and v-else-if directives whereas v-show doesn't support else directives.
        3. v-if has higher toggle costs while v-show has higher initial render costs. i.e, v-show has a performance advantage if the elements are switched on and off frequently, while the v-if has the advantage when it comes to initial render time.
        4. v-if supports <template> tab but v-show doesn't support.
6.  ### What is the purpose of v-for directive?
    The built-in v-for directive allows us to loop through items in an array or object. You can iterate on each element in the array or object.
    1. Array usage:
    ```javascript
    <ul id="list">
      <li v-for="(item, index) in items">
        {{ index }} - {{ item.message }}
      </li>
    </ul>

    var vm = new Vue({
      el: '#list',
      data: {
        items: [
          { message: 'John' },
          { message: 'Locke' }
        ]
      }
    })
    ```
    You can also use `of` as the delimiter instead of `in`, similar to javascript iterators.
    2. Object usage:
    ```javascript
    <div id="object" v-for="(value, key, index) in object">
      {{ index }}. {{ key }}: {{ value }}
    </div>

    var vm = new Vue({
      el: '#object',
      data: {
        user: {
          firstName: 'John',
          lastName: 'Locke',
          age: 30
        }
      }
    })
    ```
7.  ### What is vue instance?
    Every Vue application works by creating a new Vue instance with the Vue function. Generally the variable vm (short for ViewModel) is used to refer Vue instance. You can create vue instance as below,
    ```javascript
    var vm = new Vue({
      // options
    })
    ```
    As mentioned in the above code snippets, you need to pass options object. You can find the full list of options in the API reference.
8.  ### How do you achieve conditional group of elements?
    You can achieve conditional group of elements(toggle multiple elements at a time) by applying **v-if** directive on `<template>` element which works as invisible wrapper(no rendering) for group of elements. For example, you can conditionally group user details based on valid user condition
    ```javascript
    <template v-if="condition">
      <h1>Name</h1>
      <p>Address</p>
      <p>Contact Details</p>
    </template>
    ```
9.  ### How do you reuse elements with key attribute?
    Vue always try to render elements as efficient as possible. So it tries to reuse the elements instead of building them from scratch. But this behavior may cause problems in few scenarios. For example, if you try to render the same input element in both `v-if` and `v-else` blocks then it holds the previous value as below,
    ```javascript
    <template v-if="loginType === 'Admin'">
      <label>Admin</label>
      <input placeholder="Enter your ID">
    </template>
    <template v-else>
      <label>Guest</label>
      <input placeholder="Enter your name">
    </template>
    ```
    In this case, it shouldn't reuse. We can make both input elements as separate by applying **key** attribute as below,
    ```javascript
        <template v-if="loginType === 'Admin'">
          <label>Admin</label>
          <input placeholder="Enter your ID" key="admin-id">
        </template>
        <template v-else>
          <label>Guest</label>
          <input placeholder="Enter your name" key="user-name">
        </template>
    ```
    The above code make sure both inputs are independent and doesn't impact each other.
10. ### Why should not use if and for directives together on the same element?
    It is recommended not to use v-if on the same element as v-for. Because v-for directive has a higher priority than v-if. There are two cases where developers try to use this combination,
    1. To filter items in a list
     For example, if you try to filter the list using v-if tag,
     ```javascript
     <ul>
       <li
         v-for="user in users"
         v-if="user.isActive"
         :key="user.id"
       >
         {{ user.name }}
       <li>
     </ul>
     ```
     This can be avoided by preparing the filtered list using computed property on the initial list
     ```javascript
     computed: {
       activeUsers: function () {
         return this.users.filter(function (user) {
           return user.isActive
         })
       }
     }
     ...... //
     ...... //
     <ul>
       <li
         v-for="user in activeUsers"
         :key="user.id">
         {{ user.name }}
       <li>
     </ul>

     ```
    2. To avoid rendering a list if it should be hidden
     For example, if you try to conditionally check if the user is to show or hide
     ```javascript
     <ul>
       <li
         v-for="user in users"
         v-if="shouldShowUsers"
         :key="user.id"
       >
         {{ user.name }}
       <li>
     </ul>
     ```
     This can be solved by moving the condition to a parent by avoiding this check for each user
     ```javascript
     <ul v-if="shouldShowUsers">
       <li
         v-for="user in users"
         :key="user.id"
       >
         {{ user.name }}
       <li>
     </ul>
     ```
11.  ### Why do you need to use key attribute on for directive?
     In order to track each node’s identity, and thus reuse and reorder existing elements, you need to provide a unique `key` attribute for each item with in `v-for` iteration. An ideal value for key would be the unique id of each item. Let us take an example usage,
     ```javascript
     <div v-for="item in items" :key="item.id">
       {{item.name}}
     </div>
     ```
     Hence, It is always recommended to provide a key with v-for whenever possible, unless the iterated DOM content is simple.
     **Note:** You shouldn’t use non-primitive values like objects and arrays as v-for keys. Use string or numeric values instead.
12.  ### What are the array detection mutation methods?
     As the name suggests, mutation methods modifies the original array. Below are the list of array mutation methods which trigger view updates.
     1. push()
     2. pop()
     3. shift()
     4. unshift()
     5. splice()
     6. sort()
     7. reverse()
     If you perform any of the above mutation method on the list then it triggers view update. For example, push method on array named 'items' trigger a view update,
     ```javascript
     vm.todos.push({ message: 'Baz' })
     ```
13.  ### What are the array detection non mutation methods?
     The methods which do not mutate the original array but always return a new array are called non-mutation methods. Below are the list of non-mutation methods,
     1. filter()
     2. concat()
     3. slice()
     For example, lets take a todo list where it replaces the old array with new one based on status filter,
     ```javascript
     vm.todos = vm.todos.filter(function (todo) {
       return todo.status.match(/Completed/)
     })
     ```
     This approach won't re-render the entire list due to VueJS implementation.
14.  ### What are the caveats of array changes detection?
     Vue cannot detect changes for the array in the below two cases,

     1. When you directly set an item with the index,For example,
        ```javascript
        vm.tods[indexOfTodo] = newTodo
        ```
     2. When you modify the length of the array, For example,
      ```javascript
      vm.todos.length = todosLength
      ```
     You can overcome both the caveats using `set` and `splice` methods, Let's see the solutions with an examples,
     **First use case solution**
     ```javascript
     // Vue.set
     Vue.set(vm.todos, indexOfTodo, newTodoValue)
     (or)
     // Array.prototype.splice
     vm.todos.splice(indexOfTodo, 1, newTodoValue)
     ```
     **Second use case solution**
     ```javascript
     vm.todos.splice(todosLength)
     ```
15.  ### What are the caveats of object changes detection?
     Vue cannot detect changes for the object in property addition or deletion., Lets take an example of user data changes,
     ```javascript
     var vm = new Vue({
       data: {
         user: {
           name: 'John'
         }
       }
     })

     // `vm.name` is now reactive

     vm.email = john@email.com // `vm.email` is NOT reactive
     ```
     You can overcome this scenario using the Vue.set(object, key, value) method or Object.assign(),
     ```javascript
     Vue.set(vm.user, 'email', john@email.com);
     (or)
     vm.user = Object.assign({}, vm.user, {
       email: john@email.com
     })
     ```
16.  ### How do you use for directive with a range?
     You can also use integer type(say 'n') for v-for directive which repeat the element many times.
     ```javascript
     <div>
       <span v-for="n in 20">{{ n }} </span>
     </div>
     ```
     It displays the number 1 to 20.
17.  ### How do you use for directive on template?
     Just similar to v-if directive on template, you can also use a <template> tag with v-for directive to render a block of multiple elements. Let's take a todo example,
     ```javascript
     <ul>
       <template v-for="todo in todos">
         <li>{{ todo.title }}</li>
         <li class="divider"></li>
       </template>
     </ul>
     ```
18.  ### How do you use event handlers?
     You can use event handlers in vue similar to plain javascript. The method calls also support the special $event variable.
     ```javascript
     <button v-on:click="show('Welcome to VueJS world', $event)">
       Submit
     </button>

     \\\\
     methods: {
       show: function (message, event) {
         // now we have access to the native event
         if (event) event.preventDefault()
         console.log(message);
       }
     }
     ```
19.  ### What are the event modifiers provided by vue?
     Normally, javascript provides event.preventDefault() or event.stopPropagation() inside event handlers. You can use methods provided by vue, but these methods are meant for data logic instead of dealing with DOM events. Vue provides below event modifiers for v-on and these modifiers are directive postfixes denoted by a dot.
     1. .stop
     2. .prevent
     3. .capture
     4. .self
     5. .once
     6. .passive
     Let's take an example of stop modifier,
     ```javascript
     <!-- the click event's propagation will be stopped -->
     <a v-on:click.stop="methodCall"></a>
     ```
     You can also chain modifiers as below,
     ```javascript
     <!-- modifiers can be chained -->
     <a v-on:click.stop.prevent="doThat"></a>
     ```
20.  ### What are key modifiers?
     Vue supports key modifiers on `v-on` for handling keyboard events. Let's take an example of keyup event with enter keycode
     ```javascript
     <!-- only call `vm.show()` when the `keyCode` is 13 -->
     <input v-on:keyup.13="show">
     ```
     Remembering all the keycodes is really difficult. It supports the full list of keycode aliases
     1. .enter
     2. .tab
     3. .delete (captures both “Delete” and “Backspace” keys)
     4. .esc
     5. .space
     6. .up
     7. .down
     8. .left
     9. .right

     Now the above keyup code snippet can be written with aliases as follows,
     ```javascript
     <input v-on:keyup.enter="submit">
     (OR)
     <!-- with shorthand notation-->
     <input @keyup.enter="submit">
     ```
21.  ### How do you define custom key modifier aliases?
     You can define custom key modifier aliases via the global `config.keyCodes`. There are few guidelines for the properties
     1. You can't use cameCase, instead you can use kebab-case with double quotation marks
     2. You can define multiple values in ann array format
     ```javascript
     Vue.config.keyCodes = {
       f1: 112,
       "media-play-pause": 179,
       down: [40, 87]
     }
     ```
22.  ### What are the supported System Modifier Keys?
     Vue supports below modifiers to trigger mouse or keyboard event listeners when the corresponding key is pressed,
     1. .ctrl
     2. .alt
     3. .shift
     4. .meta
     Lets take an example of control modifier with click event,
     ```javascript
     <!-- Ctrl + Click -->
     <div @click.ctrl="doSomething">Do something</div>
     ```
23.  ### What are the supported Mouse Button Modifiers?
     Vue supports below mouse button modifiers
     1. .left
     2. .right
     3. .middle
     For example, the usage of `.right` modifier as below
     ```javascript
      <button v-if="button === 'right'"
                 v-on:mousedown.right="increment" v-on:mousedown.left="decrement" />
     ```
24.  ### How do you implement two way binding?
     You can use the `v-model` directive to create two-way data bindings on form input, textarea, and select elements. Lets take an example of it using input component,
     ```javascript
     <input v-model="message" placeholder="Enter innput here">
     <p>The message is: {{ message }}</p>
     ```
     Remember, v-model will ignore the initial value, checked or selected attributes found on any form elements. So it always use the Vue instance data as the source of truth.
25.  ### What are the supported modifiers on model?
     There are three modifiers supported for v-model directive.
     **1. lazy:** By default, v-model syncs the input with the data after each input event. You can add the lazy modifier to instead sync after change events.
     ```javascript
     <!-- synced after "change" instead of "input" -->
     <input v-model.lazy="msg" >
     ```
     **2. number:** If you want user input to be automatically typecast as a number, you can add the number modifier to your v-model. Even with type="number", the value of HTML input elements always returns a string. So, this typecast modifier is required.
     ```javascript
     <input v-model.number="age" type="number">
     ```
     **3. trim:** If you want whitespace from user input to be trimmed automatically, you can add the trim modifier to your v-model.
     ```javascript
     <input v-model.trim="msg">
     ```
26.  ### What are components and give an example?
     Components are reusable Vue instances with a name. They accept the same options as new Vue, such as data, computed, watch, methods, and lifecycle hooks(except few root-specific options like el). Lets take an example of counter component,
     ```javascript
     // Define a new component called button-counter
     Vue.component('button-counter', {
       template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>'
       data: function () {
         return {
           count: 0
         }
       },
     })
     ```
     Let's use this component inside a root Vue instance created with new Vue
     ```javascript
     <div id="app">
       <button-counter></button-counter>
     </div>

     var vm = new Vue({ el: '#app' });
     ```

