<template>
  <div class="col-sm-12 col-md-4">
    <div class="cat-card">
      <div class="card" :class="getCatAffectionClass(cat)" v-if="cat.affection!=0">
        <!-- v ATTRIBUTE BINDING -->
        <img :src="cat.img" height="20" class="img-fluid rounded-top" alt="">
        <div class="card-body">
          <!-- HANDLEBARS TEMPLATING -->
          <h1>{{cat.name}} - {{cat.affection}}</h1>
          <div>
            <button class="btn btn-dark text-uppercase " @click="pet()" :disabled="cat.affection==0">Pet</button>
            <button class="btn btn-dark text-uppercase ms-3" @click="cat.affection = 5">Give Catnip</button>
          </div>
        </div>
      </div>
      <div v-else>
        <h3>THE CAT HAS RAN AWAY!!! 😢</h3>
      </div>
    </div>
  </div>
</template>


<script>
import { Cat } from '../models/Cat.js'

export default {
  props: {
    cat: { type: Cat, required: true }
  },
  setup(props) {
    const cat = props.cat
    return {
      pet() {
        cat.affection += Math.round(Math.random() * 2) - 1
        if (cat.affection > 7) {
          cat.affection = 7
        }
        if (cat.affection < 0) {
          cat.affection = 0
        }
        console.log(cat.affection);
      },
      getCatAffectionClass(cat) {
        if (cat.affection >= 6) {
          return 'bg-success'
        }
        if (cat.affection <= 2) {
          return 'bg-danger'
        }


        return 'bg-dark'
      }
    }
  }
}
</script>


<style lang="scss" scoped>

</style>
