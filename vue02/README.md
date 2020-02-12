<h1>Card Shopping </h1>

### Screenshot
![vuejs02](https://user-images.githubusercontent.com/34090058/74372582-f9b0fa80-4deb-11ea-82a5-83b4ce32a77c.gif)

# Code Example

 app.js
  ```js
window.addEventListener('load', () => {

    window.vue = new Vue({
      el: '#app',
      name: 'Cart',
      data: {
        isLoading: true,
        cart: [],
        saved: []
      },
      methods: {
        removeFromCart(index) {
          this.cart.splice(index, 1);
        },
        saveForLater(index) {
          const item = this.cart.splice(index, 1);
          this.saved.push(item[0]);
        },
        removeFromSavedList(index) {
          this.saved.splice(index);
        },
        moveToCart(index) {
          const item = this.saved.splice(index, 1);
          this.cart.push(item[0]);
        }
      },
      created() {
        fetch('./data.json')
          .then((res) => { return res.json() })
          .then((res) => {
            this.isLoading = false;
            this.cart = res.cart;
            this.saved = res.saved;
          })
      }
    })
  
  });
   ```
   
   ## How to Run to Server
 ```
 python -m SimpleHTTPServer 8000
 ```
