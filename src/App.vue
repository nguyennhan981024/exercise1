<template>
  <div class="container content">
   <Header class="mt-3" :currentPage="currentPage" :totalPage="totalPage" :step="step"/>

   <AboutYou v-if="currentPage === 1"/>
    <AboutCompany v-if="currentPage === 2"/>
    <Finishing v-if="currentPage === 3"/>
    <Footer :next-process="nextProcess" :currentPage="currentPage" :totalPage="totalPage" :prev-process="prevProcess" :reset-process="resetProcess"/>
  </div>
</template>
<script>


import Header from "@/components/Header";
import AboutYou from "@/components/AboutYou";
import AboutCompany from "@/components/AboutCompany";
import Footer from "@/components/Footer";
import Finishing from "@/components/Finishing";
export default {
  components: {Finishing, Footer, AboutCompany, AboutYou, Header},
  data(){
    return {
      currentPage : 1,
      progress: 0,
      totalPage  : 3,
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
}
</style>
