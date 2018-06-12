<template>
  <div id="app">
    <home />
    <about />
    <arsenal />
    <work />
    <people />
    <contact />
    <router-view/>
  </div>
</template>


<script>
import home from '@/components/Header.vue'
import about from '@/components/About.vue'
import arsenal from '@/components/Arsenal.vue'
import work from '@/components/Work.vue'
import people from '@/components/People.vue'
import contact from '@/components/Contact.vue'

export default {
  name: 'App',
  components: {
    home, about, arsenal,work,people,contact
  },
  data() {
    return {
    }
  }
}
</script>

<style>
@import url('https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css');
@import url('https://fonts.googleapis.com/css?family=Josefin+Sans');
@import url('./assets/animate.css');
body {
  font-family: Josefin Sans;
  /*--fixes the gap between components--*/
  background-color: #293a3f;
}


</style>
