<template>
  <div class="card">
    <img :src="image" alt="Avatar" style="width:100%">
    <div class="container">
        <h4><b>{{name}}</b></h4>
        <p>{{age}}</p>
        <p>{{email}}</p>
    </div>
  </div>
</template>

<script>
const axios = require('axios');
import { ref } from "vue";
export const data = {};

export default {
    name: "Card",
    setup(){
        const data = ref({});
        const image = ref('');
        const age = ref('');
        const name = ref('');
        const email = ref('');
        return {
            data, image, age, name, email
        }
    },
    beforeMount(){
        this.getInfo();
    },
    methods: {
       async getInfo(){
            const { data } = await axios.get('https://randomuser.me/api/');
                console.log(data);
                let profile = data.results[0];
                let { gender, name, email, dob, phone, picture } = profile;
                this.data =  { gender, name, email, dob, phone, picture };
                this.image = picture.large;
                this.name = `${name.title} ${name.first} ${name.last}`;
                this.age = dob.age;
                this.email = email;
        }
    }
}
</script>

<style>
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
</style>