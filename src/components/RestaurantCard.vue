<template>
  <div class="restaurant--card">
    <div :style="ChangeBackground" class="restaurant--image">

    </div>
    <div class="restaurant--informations">
        <div class="top">
            <p class="name">
                {{  info_restaurant.name}}
            </p>
            <p class="note">
                <span>
                    {{  info_restaurant.note}}
                </span>
        </p>
        </div>
        <p class="time">
            {{  info_restaurant.drive_time}}
        </p>
    </div>
  </div>
</template>

<script>
import { computed } from 'vue';
export default {
    name: "RestaurantCard",
    props : {
        info_restaurant : Object
    },
    setup(props) {
        const ChangeBackground =computed(() => {
            return {
                backgroundImage: `url(${props.info_restaurant.image})`
            }
        })
        return {
            ChangeBackground
        }
    }
}
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
        }
    }
}

</style>