<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">
      人氣餐廳
    </h1>
    
    <hr>
    <div
      v-for="restaurant in restaurants"
      :key="restaurant.id"
      class="card mb-3"
      style="max-width: 540px;margin: auto;"
    >
      <div class="row no-gutters">
        <div class="col-md-4">
          <a href="#">
            <img
              class="card-img"
              :src="restaurant.image"
            >
          </a>
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">
              {{restaurant.name}}
            </h5>
            <span class="badge badge-secondary">收藏數：{{restaurant.FavoriteCount}}</span>
            <p class="card-text">
              {{restaurant.description}}
            </p>
            <a
              href="#"
              class="btn btn-primary mr-2"
            >Show</a>

            <button
              v-if="restaurants.isFavorited"
              type="button"
              class="btn btn-danger mr-2"
              @click.prevent.stop="deleteFavorite"
            >
              移除最愛
            </button>
            <button
              v-else
              type="button"
              class="btn btn-primary"
              @click.prevent.stop="addFavorite"
            >
              加到最愛
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import NavTabs from './../components/NavTabs'

const dummyData = {
    "restaurants": [
        {
            "id": 50,
            "name": "Jeffery Schinner IV",
            "tel": "262.066.7164 x6800",
            "address": "3442 Sigurd Lock",
            "opening_hours": "08:00",
            "description": "Eveniet sint accusantium.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=57.27823250052164",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 49,
            "name": "Maverick Hegmann",
            "tel": "605-681-2384 x139",
            "address": "15690 Keshaun Motorway",
            "opening_hours": "08:00",
            "description": "Vitae autem totam ut repudiandae perferendis quam ",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=95.71365060812892",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 1,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 48,
            "name": "Mr. Vallie Huel",
            "tel": "558.507.1283 x9863",
            "address": "120 Torphy Gardens",
            "opening_hours": "08:00",
            "description": "Consequatur voluptatem non at libero incidunt qui ",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=31.818582844357145",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 2,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 47,
            "name": "Angelina Hirthe",
            "tel": "(298) 131-1288 x40065",
            "address": "573 Kutch Terrace",
            "opening_hours": "08:00",
            "description": "Consequatur alias esse. Enim necessitatibus aliqua",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=38.39765966271364",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 1,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 46,
            "name": "Jamie Anderson",
            "tel": "448.853.6355 x4613",
            "address": "360 Bruen Shoal",
            "opening_hours": "08:00",
            "description": "Voluptas in a dolorem autem eveniet mollitia exped",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=29.79983980978591",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 1,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 45,
            "name": "Rashad McKenzie",
            "tel": "030-774-7461 x63957",
            "address": "759 Judge Run",
            "opening_hours": "08:00",
            "description": "Magnam non vel dignissimos ut cum ut officiis eos ",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=17.431614784562143",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 44,
            "name": "Dr. Vernice Stanton",
            "tel": "(988) 985-4625 x0128",
            "address": "6623 Kurt Cape",
            "opening_hours": "08:00",
            "description": "Inventore voluptatem porro est nemo laudantium nih",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=27.53134764045648",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 4,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 43,
            "name": "Cole Gerhold",
            "tel": "106.246.2927",
            "address": "395 Sporer Field",
            "opening_hours": "08:00",
            "description": "ullam velit nesciunt",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=48.1709023276637",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 42,
            "name": "Hector Donnelly PhD",
            "tel": "676.853.0476 x597",
            "address": "77073 Nader Shores",
            "opening_hours": "08:00",
            "description": "Est iusto animi eos incidunt doloremque optio alia",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=73.4416417473136",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 41,
            "name": "Gladyce Yundt",
            "tel": "659-260-0750 x867",
            "address": "82081 Bryon Well",
            "opening_hours": "08:00",
            "description": "Rerum ducimus et.\nDelectus eos quia officiis ipsa ",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=72.33184972914239",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 3,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        }
    ]
}


export default {
  name:'RestaurantsTop',
  components: {
    NavTabs
  },


  data () {
    return {
      restaurants: [],
      
    }
  },
  created(){
    this.fetchRestaurants()
  },
  methods:{
    fetchRestaurants(){
      this.restaurants= dummyData.restaurants
    },
    addFavorite () {
      this.restaurant = {
        ...this.restaurant, // 保留餐廳內原有資料
        isFavorited: true
      }
    },
    deleteFavorite () {
      this.restaurant = {
        ...this.restaurant, // 保留餐廳內原有資料
        isFavorited: false
      }},
  }
}
</script>
