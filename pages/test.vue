<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
     
      <h1>Test</h1>

      <ul class="py-12">
        <li v-for='(buzzword, index) in buzzwords' :key="buzzword" :class="{ active: index === activePosition }">
          {{ buzzword }} 
        </li>
      </ul>

    </v-col>
  </v-row>
</template>



<script>
export default {
  data() {
    return {
      activePosition: 0,
      buzzwords: [ 'Eins', 'Zwei', 'Drei und noch was' ]
    }
  },
  mounted(){ 
    this.changeActivePosition()
  },
  methods:{
    changeActivePosition(){
      this.activePosition = (this.activePosition + 1) % this.buzzwords.length
      setTimeout(this.changeActivePosition, 1000)

    }
  }
  
}
</script>

<style>

.active{
  font-weight:bold;
}

</style>