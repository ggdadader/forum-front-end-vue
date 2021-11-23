<template>
  <div class="row no-gutters">
    <div class="col-md-4">
        <img :src="userProfile.image | emptyImage" width="300px" height="300px">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title">{{userProfile.name}}</h5>
        <p class="card-text">
          {{userProfile.email}}
        </p>
        <ul class="list-unstyled list-inline">
         <li><strong>{{userProfile.commentsLength}}</strong> 已評論餐廳</li>
          <li><strong>{{userProfile.favoritedRestaurantsLength}}</strong> 收藏的餐廳</li>
          <li><strong>{{userProfile.followingsLength}}</strong> followings (追蹤者)</li>
          <li><strong>{{userProfile.followersLength}}</strong> followers (追隨者)</li>
        </ul>
        <p>
              </p><form action="/following/2" method="POST" style="display: contents;">
              <button
              v-if="isFollowed" 
              type="submit" 
              class="btn btn-danger" @click.stop.prevent="deleteFollowing">取消追蹤</button>
              <button 
              v-else
              type="submit" class="btn btn-primary" @click.stop.prevent="addFollowing">追蹤</button>
              </form>
        <p></p>
      </div>
    </div>
  </div>
</template>


<script >
import { emptyImageFilter } from './../utils/mixins'
export default {
  mixins: [emptyImageFilter],
  props: {
    userProfile: {
      type: Object,
      required: true
    },
    initalIsFollowed:{
      type:Boolean,
      dafault:false,
    }
  },
  data () {
    return {
      isFollowed: this.initialIsFollowed
    }
  },
  methods: {
     addFollowing () {
      this.isFollowed = true
      
    },
    deleteFollowing () {
      this.isFollowed = false
    },

   
  }
}
</script>