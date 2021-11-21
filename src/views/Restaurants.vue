<template>
  <div class="container py-5">
    <NavTabs />
    <!-- 餐廳類別標籤 RestaurantsNavPills -->
    <RestaurantsNavPills :categories="categories" />

    <div class="row">
      <!-- 餐廳卡片 RestaurantCard-->
      <RestaurantCard
      v-for="restaurant in restaurants"
      :key="restaurant.id"
      :initial-restaurant = "restaurant" />
    </div>

    <!-- 分頁標籤 RestaurantPagination -->
    <RestaurantsPagination
      v-if="totalPage.length > 1"
      :current-page="currentPage"
      :total-page="totalPage"
      :category-id="categoryId"
      :previous-page="previousPage"
      :next-page="nextPage"
    />
  </div>
</template>

<script>
import NavTabs from './../components/NavTabs'
import RestaurantCard from './../components/RestaurantCard.vue'
import RestaurantsNavPills from './../components/RestaurantsNavPills.vue'
import RestaurantsPagination from './../components/RestaurantsPagination.vue'

const dummyData = {
    "restaurants": [
        {
            "id": 1,
            "name": "Mathilde Marks",
            "tel": "(448) 250-2071 x8127",
            "address": "122 Crooks Course",
            "opening_hours": "08:00",
            "description": "Velit est ut labore id vero earum nobis fugiat asp",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=57.51093863724223",
            "viewCounts": 0,
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-10T20:54:42.000Z",
                "updatedAt": "2021-11-10T20:54:42.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 2,
            "name": "Judah Sporer",
            "tel": "1-465-198-1632",
            "address": "0721 Stamm Dam",
            "opening_hours": "08:00",
            "description": "Consequatur veniam eius voluptas autem illo dolore",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=59.6988073109493",
            "viewCounts": 0,
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2021-11-10T20:54:42.000Z",
                "updatedAt": "2021-11-10T20:54:42.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 3,
            "name": "Santino Sawayn",
            "tel": "(036) 355-0369 x830",
            "address": "561 Amelie Port",
            "opening_hours": "08:00",
            "description": "quia placeat repellendus",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=54.592091954605706",
            "viewCounts": 0,
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2021-11-10T20:54:42.000Z",
                "updatedAt": "2021-11-10T20:54:42.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 4,
            "name": "Mylene Champlin",
            "tel": "518-419-7198 x59022",
            "address": "247 Kenna Route",
            "opening_hours": "08:00",
            "description": "laboriosam",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=2.4272332206076275",
            "viewCounts": 0,
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2021-11-10T20:54:42.000Z",
                "updatedAt": "2021-11-10T20:54:42.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 5,
            "name": "Abelardo Torp",
            "tel": "204.155.1324",
            "address": "88542 Earlene Pike",
            "opening_hours": "08:00",
            "description": "qui et nesciunt",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=3.4964271722441875",
            "viewCounts": 0,
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2021-11-10T20:54:42.000Z",
                "updatedAt": "2021-11-10T20:54:42.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 6,
            "name": "Alana Cummings",
            "tel": "1-880-002-3513 x43273",
            "address": "2329 Kacie Route",
            "opening_hours": "08:00",
            "description": "Ea corporis suscipit sunt ut repellendus rerum. Ve",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=75.14824688340225",
            "viewCounts": 0,
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2021-11-10T20:54:42.000Z",
                "updatedAt": "2021-11-10T20:54:42.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 7,
            "name": "Vivienne Krajcik",
            "tel": "206.216.7922",
            "address": "749 Hackett Hollow",
            "opening_hours": "08:00",
            "description": "Commodi accusantium rerum qui amet excepturi. Repe",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=36.90261676536035",
            "viewCounts": 0,
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2021-11-10T20:54:42.000Z",
                "updatedAt": "2021-11-10T20:54:42.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 8,
            "name": "Waldo Mayer",
            "tel": "765-164-8905 x9049",
            "address": "1508 Lane Station",
            "opening_hours": "08:00",
            "description": "Exercitationem officia dolore facilis laboriosam v",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=50.746170674635806",
            "viewCounts": 0,
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2021-11-10T20:54:42.000Z",
                "updatedAt": "2021-11-10T20:54:42.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 9,
            "name": "Marvin Mante",
            "tel": "307.313.5867",
            "address": "585 Mazie Bridge",
            "opening_hours": "08:00",
            "description": "Et repudiandae quas consequuntur non nisi id iste ",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=45.831486647238684",
            "viewCounts": 0,
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2021-11-10T20:54:42.000Z",
                "updatedAt": "2021-11-10T20:54:42.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 10,
            "name": "Aron Langworth",
            "tel": "847-551-7048 x526",
            "address": "384 Harber Cape",
            "opening_hours": "08:00",
            "description": "Vero explicabo labore eius ut voluptas non amet do",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=55.48890726344453",
            "viewCounts": 0,
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2021-11-10T20:54:42.000Z",
                "updatedAt": "2021-11-10T20:54:42.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        }
    ],
    "categories": [
        {
            "id": 1,
            "name": "中式料理",
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z"
        },
        {
            "id": 2,
            "name": "日本料理",
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z"
        },
        {
            "id": 3,
            "name": "義大利料理",
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z"
        },
        {
            "id": 4,
            "name": "墨西哥料理",
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z"
        },
        {
            "id": 5,
            "name": "素食料理",
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z"
        },
        {
            "id": 6,
            "name": "美式料理",
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z"
        },
        {
            "id": 7,
            "name": "複合式料理",
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z"
        }
    ],
    "categoryId": "",
    "page": 1,
    "totalPage": [
        1,
        2,
        3,
        4,
        5
    ],
    "prev": 1,
    "next": 2
}
export default {
  components: {
    NavTabs:NavTabs,
    RestaurantCard,
    RestaurantsNavPills,
    RestaurantsPagination
  },
  data () {
    return {
      restaurants: [],
      categories: [],
      categoryId: -1,
      currentPage: 1,
      totalPage: [],
      previousPage: -1,
      nextPage: -1

    }
  },
  created(){
    this.fetchRestaurants()
  },
  methods:{
    fetchRestaurants(){
      const {
        restaurants,
        categories,
        categoryId,
        page,
        totalPage,
        prev,
        next
      } = dummyData
      this.restaurants =restaurants
      this.categories = categories
      this.categoryId = categoryId
      this.currentPage = page
      this.totalPage = totalPage
      this.previousPage = prev
      this.nextPage = next
    }
  }
}
</script>