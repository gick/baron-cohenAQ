<template>
  <div class="home">
    <ul>
      <template v-for="i in [...Array(49).keys()]" v-bind:key="i">
        <Question v-bind:number="i" />
         <hr class="small">
         <br>

      </template>
    </ul>
  <div>
  <button v-on:click="computeAQ">Calculate AQ</button>
   AQ={{$store.state.AQ}}
  </div>  
  </div>
</template>

<script>
// @ is an alias to /src
import Question from "@/components/Question.vue";

export default {
  name: "Home",
  components: {
    Question,
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
</style>