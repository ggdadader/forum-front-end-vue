<template>
  <div class="container py-5">
    <AdminRestaurantForm 
    :initial-restaurant="restaurant"
    @after-submit="handleAfterSubmit" />
  </div>
</template>

<script>
import AdminRestaurantForm from './../components/AdminRestaurantForm.vue'

const dummyData ={
    "restaurant": {
        "id": 1,
        "name": "Flossie Lueilwitz",
        "tel": "1-952-957-1608",
        "address": "7201 Anahi Point",
        "opening_hours": "08:00",
        "description": "Et quibusdam excepturi ea. Laboriosam accusantium provident asperiores tempora sed rerum quia harum voluptas. Corrupti quo magnam qui animi consequuntur animi ipsum sit officia. Odit doloribus nihil. Velit at fugit aliquam officiis dolorem suscipit accusamus cupiditate. Et sit sed exercitationem quia facilis.",
        "image": "https://loremflickr.com/320/240/restaurant,food/?random=23.021365402665616",
        "CategoryId": null,    
        }
}

export default {
  name:'AdminRestaurantEdit',
  props: {
    initialRestaurant:{
      type:Object,
      default:() =>({
        name:'',
        categoryId:'',
        tel:'',
        address:'',
        description:'',
        image:'',
        openingHours:''
        
      })
    }
  },
  components: {
    AdminRestaurantForm
  },
  
  data(){
    return{
      categories: [],
      restaurant:{
        ... this.initialRestaurant,
        
      }
    }
  },
  created (){
    const {id} = this.$route.params
    this.fatchRestaurant(id)  
  }
  ,


 

  methods: {
     fatchRestaurant (restaurantId){
    console.log('fetchRestaurant id:', restaurantId)
    const {restaurant} = dummyData
    const {id, name, CategoryId:categoryId, tel, address,opening_hours:openingHours,description, image, }=restaurant
    this.restaurant ={
      ...this.restaurant,
      id,
      name,
      categoryId,
      tel,
      address,
      description,
      image,
      openingHours
    }
  }
  ,
    handleAfterSubmit (formData) {
      // 透過 API 將表單資料送到伺服器
      for (let [name, value] of formData.entries()) {
        console.log(name + ': ' + value)
      }
    }
  }
}
</script>