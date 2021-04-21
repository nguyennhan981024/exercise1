<template>
    <div class="container content">
      <Header class="mt-3" :currentPage="currentPage" :totalPage="totalPage" :step="step"/>
      <Body :currentPage="currentPage"
            :next-process="nextProcess" :totalPage="totalPage" :prev-process="prevProcess" :reset-process="resetProcess" :finish-process="finishProcess"
      />
    </div>
</template>
<script>


import Header from "@/components/Header";
import Body from "./components/Body";
export default {
  components: {Header,Body},
  data(){
    return {
      currentPage : 1,
      progress: 0,
      totalPage  : 3,
      formStatus : false,
      step : [{
        step : 1,
        status : true,
        text : 'about you'
      },
        {
          step : 2,
          status : false,
          text : 'about your company'
        },
        {
          step : 3,
          status : false,
          text : 'finishing up'
        }

      ],
    }
  },
  methods:{
    nextProcess(){
      this.currentPage === this.totalPage ? this.currentPage = this.totalPage : this.currentPage ++
      this.step = [...this.step].map(item => {
        if(item.step === this.currentPage) {
          item.status = true
        }
        return item
      })
    },
    prevProcess(){

      if(this.currentPage > 1){
        this.step = [...this.step].map(item => {
          if(item.step === this.currentPage) {
            item.status = false
          }
          return item
        })
      }
      this.currentPage === 1 ? this.currentPage = 1 : this.currentPage --
    },
    resetProcess(){

      this.currentPage = 1
      this.step = [...this.step].map(item => {
        if(item.step !== this.currentPage){
          item.status = false;
        }
        return item
      })
    },
    finishProcess(){
      alert('The form submit successfully')
    }
  },

}
</script>

<style>
.content {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #a3aaaf;
  margin-top: 60px;
  text-transform: capitalize;
}
</style>
