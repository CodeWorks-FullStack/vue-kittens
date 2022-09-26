<template>
  <div>

    <div class="container-fluid my-4">
      <div class="row">
        <CatCard v-for="c in cats" :cat="c" class="mb-3" />
      </div>
    </div>

  </div>
</template>

<script>
// YOUR NEW CONTROLLER
// SINGLE COMPONENT FILES
// WHAT IS A COMPONENT?
//  A COMPONENT IS

import { AppState } from '../AppState.js'

// A TEMPLATE + A CONTROLLER
export default {
  // REVIEW for additional reading Factory Pattern is utilized under the hood.... you know if you want...
  setup() { // kinda like your new constructor.... Thanks Tom
    let cat = AppState.cat
    let cats = AppState.cats
    // always the last thing the setup must do
    return {
      cats,
      cat,
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
      getCatAffectionClass() {
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

<style scoped lang="scss">
.home {
  display: grid;
  height: 80vh;
  place-content: center;
  text-align: center;
  user-select: none;

  .home-card {
    width: 50vw;

    >img {
      height: 200px;
      max-width: 200px;
      width: 100%;
      object-fit: contain;
      object-position: center;
    }
  }
}
</style>
