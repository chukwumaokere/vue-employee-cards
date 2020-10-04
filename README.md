# employee-card

employee-cards
* [ ] Create a new vue3 project named "employee-cards"
* [ ] Delete the helloworld component and any references to it
* [ ] Create a git repo for "employee-cards" 
* [ ] Link the new project to the git repo
* [ ] Push an initial commit AFTER you've deleted the helloworld basic components
* [ ] Install axios "npm install axios"
* [ ] Create a Card component 
* [ ] Use axios in that card component to fetch random data from this api: https://randomuser.me/api/
* [ ] Add these styles to the card component
```css
.card {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  border-radius: 5px; /* 5px rounded corners */
  width: 100%;
  margin: 5%;
}

img {
  border-radius: 5px 5px 0 0;
}

/* On mouse-over, add a deeper shadow */
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}

/* Add some padding inside the card container */
.container {
  padding: 2px 16px;
}
```
* [ ] The template should follow this styling: 

```html
<div class="card">
    <img :src="image" alt="Avatar" style="width:100%">
    <div class="container">
        <h4><b> PERSONS NAME (FIRST AND LAST NAME AND TITLE) </b></h4>
        <p> (PERSONS AGE) </p>
        <p> (PERSONS EMAIL ADDRESS) </p>
    </div>
  </div>
```
NOTE we use :src so we can bind the image (as a variable) from the script to the template.

* [ ] On the App.vue import your card component
* [ ] Make 3 calls to your card component so that there are 3 cards side by side on the app. (You may need to put the three calls in a div with a grid or something) 

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
