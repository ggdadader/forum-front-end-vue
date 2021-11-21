<template>
  <div class="row no-gutters">
    <div class="col-md-4">
        <img :src="userProfile.image" width="300px" height="300px">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title">{{userProfile.name}}</h5>
        <p class="card-text">
          {{userProfile.email}}
        </p>
        <ul class="list-unstyled list-inline">
          <li><strong>32</strong> {{userProfile.Comments.length }}</li>
          <li><strong>4</strong> {{userProfile.FavoritedRestaurants.length }}</li>
          <li><strong>1</strong> {{userProfile .followings.length }} (追蹤者)</li>
          <li><strong>0</strong> {{userProfile.followers.length }} (追隨者)</li>
        </ul>
        <p>
              </p><form action="/following/2" method="POST" style="display: contents;"><button type="submit" class="btn btn-primary">追蹤</button></form>
        <p></p>
      </div>
    </div>
  </div>
</template>


<script >
export default {
  props: {
    userProfile: {
      type: Object,
      required: true
    },
    isFollowed:{
      type:Boolean,
      dafalt:false,
    }
  },
  methods: {

   
  }
}
</script>