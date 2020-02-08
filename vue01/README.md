<h1>Vuejs Hello World </h1>

## Vuejs Hello World

### Screenshot

<p align="center">
  <a href="https://user-images.githubusercontent.com/34090058/74091138-50a19180-4ac5-11ea-8554-ca6997272e95.png">
    <img alt="Techs" title="Techs" src="https://user-images.githubusercontent.com/34090058/74091138-50a19180-4ac5-11ea-8554-ca6997272e95.png"width="400">
  </a>
</p>


# Code Example
index.html
 ```js
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Vue</title>
    <!-- development version, includes helpful console warnings -->
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
   
</head>
<body>
    <div id="app">
        <h1 v-if="isLoggedIn">{{message}} {{username}}</h1>
        <h1 v-if="!isLoggedIn">{{message}}</h1>

        <h1 v-show="isLoggedIn">{{message}} {{username}}</h1>
        <h1 v-show="!isLoggedIn">{{message}}</h1>
    </div>

    <script src="app.js"></script>
</body>
</html>
 ```
 app.js
  ```js
  new Vue({
    el: '#app',
    data : {
        message: "Hello World",
        username: "Kadir",
        isLoggedIn: true
    }
})
   ```