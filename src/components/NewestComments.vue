<template>
  <div class="card">
    <div class="card-header">
      最新評論
    </div>
    <div class="card-body">
      <div
        v-for="comment in comments"
        :key="comment.id"
        >
        <h4>
          <router-link
            :to="{ name:'restaurant', params: { id:comment.Restaurant.id } } "
          >
            {{ comment.Restaurant.name }}
          </router-link>
        </h4>
        <p>{{comment.text}}</p>by
        <a href="#">
          {{comment.Restaurant.name}}
        </a>
        at {{comment.creatAt | fromNow}}
        <hr>
      </div>
    </div>
  </div>
</template>

<script>
import {fromNowFilter} from './../utils/mixins'

export default {
  mixins: [fromNowFilter],
  data() {
    
  },
  props: {
    comments: {
      type: Text,
      required: true
    }
  }
}
</script>