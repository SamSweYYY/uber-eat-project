<template>
  <div class="restaurant--row">
    <h2 class="title">
        Nos Restaurants
    </h2>
    <div class="wrapper--card">
        <RestaurantCard v-for="(card, index) in three_restaurant" :info_restaurant="card" :key="index"/>
    </div>
  </div>
</template>

<script>
import RestaurantCard from './RestaurantCard';

export default {
    name: "RestaurantRow",
    components: {
        RestaurantCard
    }, 
    props: {
        three_restaurant : Array
    }
}
</script>

<style lang="scss">
.restaurant--row {
    .wrapper--card {
        display: flex;
        align-items:center;
        justify-content: space-between;
    }
}

</style>