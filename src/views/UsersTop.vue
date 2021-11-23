<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">
      美食達人
    </h1>
    <div class="row">
    <RestaurantUserTop
      v-for="user in users"
      :key="user.id"
      :initial-user= "user" />
    </div>
    
  </div>
</template>

<script>
import NavTabs from './../components/NavTabs'
import RestaurantUserTop from './../components/RestaurantUserTop.vue'
const dummyData = {
    "users": [
        {
            "id": 1,
            "name": "root",
            "email": "root@example.com",
            "password": "$2a$10$px5KV70r1X5Pkq6f5fYvvu1KIpLiEPepD5QuVyDT.Cq5i2n.3LZU2",
            "isAdmin": true,
            "image": 'https://i.pinimg.com/originals/15/14/d8/1514d8b48eab932a8325cd9da9b696a3.png',
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z",
            "Followers": [],
            "FollowerCount": 0,
            "isFollowed": false
        },
        {
            "id": 2,
            "name": "user1",
            "email": "user1@example.com",
            "password": "$2a$10$H7wKQi/UcAtXjUYIIUXJuOEQSFAL.9zhkC0UQiFcuGR9q9HbLzDU2",
            "isAdmin": false,
            "image": 'https://avatarfiles.alphacoders.com/950/95058.png',
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z",
            "Followers": [],
            "FollowerCount": 0,
            "isFollowed": false
        },
        {
            "id": 3,
            "name": "user2",
            "email": "user2@example.com",
            "password": "$2a$10$t.WvR.HMLXTF2CCz8vcwZe8eP5NzCXmke5PJtWff2e83PDjFS1NNK",
            "isAdmin": false,
            "image": 'https://66.media.tumblr.com/0386a450bbb44e34cea01a614cb9d7e9/tumblr_p6id66Y5eb1vtjnq8o1_640.jpg',
            "createdAt": "2021-11-10T20:54:42.000Z",
            "updatedAt": "2021-11-10T20:54:42.000Z",
            "Followers": [],
            "FollowerCount": 0,
            "isFollowed": false
        }
    ]
}
export default {
  components: {
    NavTabs:NavTabs,
    RestaurantUserTop
  },
  data(){
  return {
    users:[],
   
  }
},
  created (){
    this.fetchUsers()
  },
  methods:{
   fetchUsers(){
      this.users =dummyData.users
    }
  }
}
</script>