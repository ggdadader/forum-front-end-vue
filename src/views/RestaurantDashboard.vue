<template>
  <div class="container py-5">
    <div>
      <h1>{{ restaurant.name }}</h1>
      <span class="badge badge-secondary mt-1 mb-3">
        {{ restaurant.categoryName }}
      </span>
    </div>

    <hr>

    <ul>
      <li>評論數： {{ restaurant.commentsLength }} </li>
      <li>瀏覽次數： {{ restaurant.viewCounts }} </li>
    </ul>

    <button
      type="button"
      class="btn btn-link"
      @click="$router.back()"
    >
      回上一頁
    </button>
  </div>
</template>

<script>
const dummyData = {
    "restaurant": {
        "id": 1,
        "name": "Mathilde Marks",
        "tel": "(448) 250-2071 x8127",
        "address": "122 Crooks Course",
        "opening_hours": "08:00",
        "description": "Velit est ut labore id vero earum nobis fugiat asperiores. Consequatur sequi est rerum dignissimos mollitia laboriosam voluptas est. Sapiente neque molestiae reprehenderit fugit quaerat expedita. Iste hic voluptatem exercitationem.",
        "image": "https://loremflickr.com/320/240/restaurant,food/?random=57.51093863724223",
        "viewCounts": 2,
        "createdAt": "2021-11-10T20:54:42.000Z",
        "updatedAt": "2021-11-16T14:51:45.000Z",
        "CategoryId": 5,
        "Category": {
            "id": 5,
            "name": "素食料理",
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z"
        },
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
    }
}
export default {
 name:"RestaurantDashboard",
 
  data(){
    return{
      restaurant: []
    }
  },
  

 
  created(){
    const { id: restaurantId } = this.$route.params;
    this.fetchRestaurant(restaurantId);
  },
  methods:{
    fetchRestaurant(restaurantId) {
      console.log("fetchRestaurant id: ", restaurantId);

      this.restaurant = {
        id: dummyData.restaurant.id,
        name: dummyData.restaurant.name,
        categoryName: dummyData.restaurant.Category.name,
        commentsLength: dummyData.restaurant.Comments.length,
        viewCounts: dummyData.restaurant.viewCounts
      };

      this.restaurantComments = dummyData.restaurant.Comments;
    },
  }
}

</script>
