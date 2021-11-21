<template>
  <div class="container py-5">
    <h1 class="d-none">餐廳描述頁</h1>
    <!-- 餐廳資訊頁 RestaurantDetail -->
    <RestaurantDetail
      :key="restaurant.id"
      :initial-restaurant = "restaurant" />
    <hr>
    <!-- 餐廳評論 RestaurantComments -->
    <RestaurantComments 
    :restaurant-comments="restaurantComments"
    @after-delete-comment="afterDeleteComment"
     />
    <!-- 新增評論 CreateComment -->
    <CreateComment 
      :restaurant-id="restaurant.id"
      @after-create-comment="afterCreateComment"
    />
  </div>
</template>

<script>
import RestaurantDetail from './../components/RestaurantDetail'
import RestaurantComments from './../components/RestaurantComments'
import CreateComment from '../components/CreateComment.vue'
const dummyData= {
    "restaurant": {
        "id": 1,
        "name": "Mathilde Marks",
        "tel": "(448) 250-2071 x8127",
        "address": "122 Crooks Course",
        "opening_hours": "08:00",
        "description": "Velit est ut labore id vero earum nobis fugiat asperiores. Consequatur sequi est rerum dignissimos mollitia laboriosam voluptas est. Sapiente neque molestiae reprehenderit fugit quaerat expedita. Iste hic voluptatem exercitationem.",
        "image": "https://loremflickr.com/320/240/restaurant,food/?random=57.51093863724223",
        "viewCounts": 1,
        "createdAt": "2021-11-10T20:54:42.000Z",
        "updatedAt": "2021-11-15T19:24:26.155Z",
        "CategoryId": 5,
        "Category": {
            "id": 5,
            "name": "素食料理",
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z"
        },
        "FavoritedUsers": [],
        "LikedUsers": [],
        "Comments": [
            {
                "id": 101,
                "text": "Rerum cumque ut porro atque et sed cum inventore et.",
                "UserId": 1,
                "RestaurantId": 1,
                "createdAt": "2021-11-10T20:54:42.000Z",
                "updatedAt": "2021-11-10T20:54:42.000Z",
                "User": {
                    "id": 1,
                    "name": "root",
                    "email": "root@example.com",
                    "password": "$2a$10$px5KV70r1X5Pkq6f5fYvvu1KIpLiEPepD5QuVyDT.Cq5i2n.3LZU2",
                    "isAdmin": true,
                    "image": null,
                    "createdAt": "2021-11-10T20:54:42.000Z",
                    "updatedAt": "2021-11-10T20:54:42.000Z"
                }
            },
            {
                "id": 51,
                "text": "Saepe eius voluptatum id.",
                "UserId": 2,
                "RestaurantId": 1,
                "createdAt": "2021-11-10T20:54:42.000Z",
                "updatedAt": "2021-11-10T20:54:42.000Z",
                "User": {
                    "id": 2,
                    "name": "user1",
                    "email": "user1@example.com",
                    "password": "$2a$10$H7wKQi/UcAtXjUYIIUXJuOEQSFAL.9zhkC0UQiFcuGR9q9HbLzDU2",
                    "isAdmin": false,
                    "image": null,
                    "createdAt": "2021-11-10T20:54:42.000Z",
                    "updatedAt": "2021-11-10T20:54:42.000Z"
                }
            },
            {
                "id": 1,
                "text": "Ea aut corrupti ut doloribus repellat.",
                "UserId": 3,
                "RestaurantId": 1,
                "createdAt": "2021-11-10T20:54:42.000Z",
                "updatedAt": "2021-11-10T20:54:42.000Z",
                "User": {
                    "id": 3,
                    "name": "user2",
                    "email": "user2@example.com",
                    "password": "$2a$10$t.WvR.HMLXTF2CCz8vcwZe8eP5NzCXmke5PJtWff2e83PDjFS1NNK",
                    "isAdmin": false,
                    "image": null,
                    "createdAt": "2021-11-10T20:54:42.000Z",
                    "updatedAt": "2021-11-10T20:54:42.000Z"
                }
            }
        ]
    },
    "isFavorited": false,
    "isLiked": false
}
const dummyUser ={
   currentUser: {
    id: 1,
    name: '管理者',
    email: 'root@example.com',
    image: 'https://i.pravatar.cc/300',
    isAdmin: true
  },
  isAuthenticated: true
}
export default {
  name: 'Restaurant',
  components:{
    RestaurantDetail,
    RestaurantComments,
    CreateComment
    
  },
  
  data() {
    return {
      restaurant: {
        id: -1,
        name: '',
        categoryName: '',
        image: '',
        openingHours: '',
        tel: '',
        address: '',
        description: '',
        isFavorited: false,
        isLiked: false
      },
      currentUser: dummyUser.currentUser,
      restaurantComments: []
    }
  },
  created () {
    const { id: restaurantId } = this.$route.params
    this.fetchRestaurant(restaurantId)
  },
  methods: {
    fetchRestaurant (restaurantId) {
      console.log('fetchRestaurant id: ', restaurantId)

      this.restaurant = {
        id: dummyData.restaurant.id,
        name: dummyData.restaurant.name,
        categoryName: dummyData.restaurant.Category.name,
        image: dummyData.restaurant.image,
        openingHours: dummyData.restaurant.opening_hours,
        tel: dummyData.restaurant.tel,
        address: dummyData.restaurant.address,
        description: dummyData.restaurant.description,
        isFavorited: dummyData.isFavorited,
        isLiked: dummyData.isLiked,
      }

      this.restaurantComments = dummyData.restaurant.Comments

  
    },
    afterDeleteComment (commentId) {
        this.restaurantComments = this.restaurantComments.filter(
          comment => comment.id !== commentId
        )
      },
    afterCreateComment (payload) {
      console.log('payload', payload)
      const { commentId, restaurantId, text } = payload
      this.restaurantComments.push({
        id: commentId,
        RestaurantId: restaurantId,
        User: {
          id: this.currentUser.id,
          name: this.currentUser.name
        },
        text,
        createdAt: new Date()
      })
    }
}
}
</script>