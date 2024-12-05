<template>
  <div class="homepage">
    <div class="header">
      <img src="https://d3i4yxtzktqr9n.cloudfront.net/web-eats-v2/ee037401cb5d31b23cf780808ee4ec1f.svg" alt="image">
      <input v-model ="user_search_restaurant" type="text" placeholder="De quoi avez-vous envie ?">
    </div>
    <div class="banner">

    </div>
    <RestaurantRow v-for="(data, i) in data_restaurant" :key="i" :three_restaurant="data"/>
  </div>
</template>

<script> 
// IMPORT
 import BDD from '../BDD';
 import { onMounted, ref, watch } from 'vue';
import RestaurantRow from '@/components/RestaurantRow.vue';

// COMPONENTS
export default {
    name: 'HomePage',
    components: {
        RestaurantRow,
    },
    setup() {
      class Restaurant {
        constructor (name, note, image, drive_time) {
          this.name = name
          this.note = note
          this.image = image
          this.drive_time = drive_time 
        }
      }
      let data_restaurant = ref([])
      let all_restaurant= []

      const makeDataRestaurant = () => {
        let three_restaurant = [];

        for (const restaurant of BDD) {
          const new_restaurant = new Restaurant(restaurant.name, restaurant.note, restaurant.image, restaurant.drive_time)
          //Make all restaurant array
          all_restaurant.push(new_restaurant)

          if(three_restaurant.length==2){
             three_restaurant.push(new_restaurant);
             data_restaurant.value.push(three_restaurant);
             three_restaurant= [];
          } else {
            three_restaurant.push(new_restaurant)
          }
        }
      }
      //User Search restaurant
      let user_search_restaurant = ref('')
      watch(user_search_restaurant, newValue => {
        
        let regex = RegExp(newValue);

        let test_array = all_restaurant.filter(restaurant => regex.test(restaurant.name))

        console.log(test_array)
      })


      onMounted(makeDataRestaurant)

      return {
        data_restaurant,
        user_search_restaurant
      }
    },
}
</script>

<style lang="scss">
.homepage {
  .header {
    height: 120px;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    img {
      width: 200px;
    }
    input {
      background-color: #f6f6f6;
      border: none;
      height: 60px;
      width: 400px;
      outline: none;
      padding-left: 20px;
    }
  }
  .banner {
    height: 200px;
    width: 100%;
    background-image:url('../assets/WelcomeToUberEats.webp');
    background-size: cover;
    background-position: center center;
    justify-content: space-around;
  }
}

</style>