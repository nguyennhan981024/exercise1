<template>
<div class="d-flex justify-content-center">
  <button class="btn btn-info" v-if="currentPage < totalPage " @click="prevProcess">previous</button>
  <button class="btn btn-primary ml-2" v-if="currentPage < totalPage" @click="nextProcess"> next</button>
  <button class="btn btn-primary ml-2" @click="resetProcess" v-if="currentPage === totalPage"> reset</button>
</div>
</template>

<script>
export default {
  name: "Footer",
  props:{
    prevProcess :{
      type : Function,
      default : () => {
        return []
      }
    },
    nextProcess: {
      type : Function,
      default : () => {
        return []
      }
    },
    resetProcess : {
      type : Function,
      default : () => {
        return []
      }
    },
    currentPage : {
      type : Number,
      default : () => {
        return 0;
      }
    },
    totalPage : {
      type : Number,
      default : () => {
        return 0;
      }
    }
  }
}
</script>

<style scoped>

</style>
