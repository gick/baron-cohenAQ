<template>
  <div class="home p-grid">
  <div class="p-col-10">
    <ul>
      <template v-for="i in [...Array(50).keys()]" v-bind:key="i">
        <Question v-bind:number="i" />
         <hr class="small">
         <br>

      </template>
    </ul>
  </div>
  <div class="p-col-3">
  <Button v-on:click="computeAQ" label="Calculer AQ" class="p-button-raised p-button-rounded" />
  </div>
  <div class="result p-col-7 p-d-flex p-jc-center p-ai-center p-text-center" v-if="$store.state.AQ>0">
  Le quotient autistique calculé à partir de vos réponse est de : {{$store.state.AQ}}    
  </div> 

  </div>
</template>

<script>
// @ is an alias to /src
import Question from "@/components/Question.vue";
import Button from 'primevue/button'
export default {
  name: "Home",
  components: {
    Question,Button
  },
  methods:{
    computeAQ(){
      this.$store.commit('computeAQ')
    }
  }
};
</script>
<style scoped>
.small{
  width:70%;
}


.result {
  font-family: "roboto";
  font-weight: bolder;
  font-size: large;
  padding: 5px;
}

</style>