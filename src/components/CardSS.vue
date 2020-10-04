<template>
  <div class="card">
    <img :src="image" alt="Avatar" style="width:100%">
    <div class="container">
        <h4><b>{{person_name}}</b></h4>
        <p>{{age}}</p>
        <p>{{person_email}}</p>
    </div>
  </div>
</template>

<script>
const axios = require('axios');
import { ref, onMounted } from "vue";

export default {
    name: "Card",
    setup(){
        let image = ref('https://previews.123rf.com/images/apoev/apoev1910/apoev191000008/132694738-person-gray-no-photo-placeholder-woman-silhouette.jpg');
        let age = ref('00');
        let person_name = ref('loading');
        let person_email = ref('loading@loading.com');
        onMounted(async () => {
            loadData();
        })
        async function loadData(){
            try{ 
                const data = await axios.get('https://randomuser.me/api/');
                console.log(data);
                let profile = data.data.results[0];
                let { 
                    //gender, 
                    name, email, dob, 
                    //phone, 
                    picture 
                } = profile;
                
                image.value = picture.large;
                person_name.value = `${name.title} ${name.first} ${name.last}`;
                age.value = dob.age;
                person_email.value = email;
                //console.log(image, age, person_email, person_name);

            }catch(err){
                person_name.value = "FAILED TO LOAD";
                age.value = "FAILED TO LOAD";
                person_email.value = "FAILED TO LOAD";
            }
        }

        return {
            image, age, person_name, person_email, loadData,
        }
    },
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