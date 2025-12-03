<template>
  <div class="restaurant--card">
    
    <router-link to="/RestaurantPage">
        <div :style="ChangeBackground" @click="clickImage" class="restaurant--image">
        </div>
    </router-link>
    <div class="restaurant--informations">
        <div class="top">
            <p class="name">
                {{  info_restaurant.name}}
            </p>  
            <span class="like">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-heart" viewBox="0 0 16 16">
  <path d="m8 2.748-.717-.737C5.6.281 2.514.878 1.4 3.053c-.523 1.023-.641 2.5.314 4.385.92 1.815 2.834 3.989 6.286 6.357 3.452-2.368 5.365-4.542 6.286-6.357.955-1.886.838-3.362.314-4.385C13.486.878 10.4.28 8.717 2.01zM8 15C-7.333 4.868 3.279-3.04 7.824 1.143q.09.083.176.171a3 3 0 0 1 .176-.17C12.72-3.042 23.333 4.867 8 15"/>
</svg>
            </span> 
        </div>
        <p class="distance">
            {{  info_restaurant.distance}}
        </p>
        <p class="time">

            {{  info_restaurant.note}}<svg xmlns="http://www.w3.org/2000/svg"  fill="currentColor" class="bi bi-star-fill" viewBox="0 0 16 16">
                <path d="M3.612 15.443c-.386.198-.824-.149-.746-.592l.83-4.73L.173 6.765c-.329-.314-.158-.888.283-.95l4.898-.696L7.538.792c.197-.39.73-.39.927 0l2.184 4.327 4.898.696c.441.062.612.636.282.95l-3.522 3.356.83 4.73c.078.443-.36.79-.746.592L8 13.187l-4.389 2.256z"/>
            </svg>
            {{  info_restaurant.drive_time}}
        </p>
    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue';

export default {
  name: "RestaurantCard",

  props: {
    info_restaurant: {
      type: Object,
      required: true
    }
  },

  setup(props) {
    // --- Background dynamique ---
    const ChangeBackground = computed(() => ({
      backgroundImage: `url(${props.info_restaurant.image})`
    }));

    // --- Gestion du clic ---
    const click = ref('');
    function clickImage() {
      
    }

    // --- Retour des variables vers le template ---
    return {
      ChangeBackground,
      click,
      clickImage
    };
  }
};
</script>


<style lang="scss">
.restaurant--card {
    width: 32%;
    height: 30vh;

    .restaurant--image {
    background-image: url('https://cn-geo1.uber.com/image-proc/resize/eats/format=webp/width=550/height=440/quality=70/srcb64=aHR0cHM6Ly9kMXJhbHNvZ25qbmczNy5jbG91ZGZyb250Lm5ldC8zNzg4MDJiMC1jNTI4LTQ4MjktYjBiNS0wY2M2NDBkZjYzY2QuanBlZw==');
    height: 70%;
    background-size: cover;
    background-position: center;
    }
    .restaurant--informations {
        .top {
            margin: 10px 0px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            .note {
                background-color: #eeeeee;
                height: 30px;
                width: 30px;
                display: flex;
                align-items: center;
                justify-content: center;
                border-radius: 50%;

            }
        }
        .time {
            font-size: 0.8rem;
            svg {
                margin: 0px 5px;
                width: 0.9rem;
                
            }
        }
        .distance {
            font-size: 0.8rem;
            margin-bottom: 5px;
        }
    }
}

</style>