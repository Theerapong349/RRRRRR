<!-- Home.vue -->
<template>
  <div class="container text-center">
    <div class="row">
      <div class="col mt-5" v-for="(restaurant, index) in travelList" :key="index">
        <div class="card" style="width: 18rem">
          <img :src="restaurant.imagesP" class="card-img-top" :width="sizeW" :height="sizeH" />
          <div class="card-body">
            <h2>สินค้าที่ : {{ index + 1 }}</h2>
            <h5 class="card-title">ชื่อสินค้า : {{ restaurant.name }}</h5>
            <p class="card-text">ราคาเริ่ม : {{ restaurant.price }}</p>
            <button
              class="btn btn-danger"
              data-bs-toggle="modal"
              data-bs-target="#staticBackdrop"
              @click="goToOtherComponent(restaurant.name, restaurant.imagesP, index)"
            >
              จองสินค้า
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue' // import ref

export default {
  methods: {
    goToOtherComponent(name, imagesP, index) {
      // ส่งค่าไปยังคอมโพเนนต์ OtherComponent.vue ผ่านคิวรี่พารามิเตอร์
      this.$router.push({
        name: 'other',
        query: {
          index: index,
          restaurantName: name,
          restaurantImagesP: imagesP
        }
      })
    }
  },
  setup() {
    const travelList = ref([
      {
        name: 'เสื้อบาส Golden State Warriors Nike',
        price: 3900,
        imagesP:
          'https://images.footballfanatics.com/golden-state-warriors/golden-state-warriors-nike-association-swingman-jersey-custom-mens_ss4_p-11995704+u-swd8rchlg5c89r0t41vb+v-db01fe95c6954473bbdb60a78ac33f81.jpg?_hv=2&w=340'
      },
      {
        name: 'Jacket Golden State Warriors Nike City Edition',
        price: 4200,
        imagesP:
          'https://images.footballfanatics.com/golden-state-warriors/golden-state-warriors-nike-city-edition-thermaflex-showtime-full-zip-jacket-black/anthracite-mens_ss4_p-13315769+u-1atdawrvudcpu9h56kcl+v-0efdf1f426ca4936bf9440559a3a2350.jpg?_hv=2&w=340'
      },
      {
        name: 'Shorts Golden State Warriors Nike Icon Swingman',
        price: 3300,
        imagesP:
          'https://images.footballfanatics.com/golden-state-warriors/golden-state-warriors-nike-icon-swingman-shorts-mens_ss4_p-12000706+u-1ah08dbic9i0nuudr1ly+v-8f359be3386240e9a835e183f38b56b2.jpg?_hv=2&w=340'
      },
      {
        name: 'Nike Basketball Shoe',
        price: 8500,
        imagesP:
          'https://images.footballfanatics.com/logo-gear/nike-basketball-shoe-zoom-lebron-nxxt-gen-mens_ss4_p-13365267+u-dc13w8k13ej1i81t3y5n+v-58295ff0be1b4d18bc91316fc326d63a.jpg?_hv=2&w=340'
      }
    ])

    const sizeW = 350
    const sizeH = 250

    return {
      // return ตัวแปรออกมาจาก setup
      travelList,
      sizeW,
      sizeH
    }
  }
}
</script>