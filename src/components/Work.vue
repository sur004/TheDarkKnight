<template>

  <div id="work">

    <p id="title">{{ title }}</p>

    <workthumbs v-if="ok" @clicked="onClickImage" />
    <workproject :ind="index" v-if="!ok" @back="onClickBack" />
    <router-view/>

  </div>

</template>

<script>
import workthumbs from '@/components/WorkThumbs.vue'
import workproject from '@/components/WorkProject.vue'

export default {
  components: {
    workthumbs,workproject
  },
  data () {
    return {
      title: 'WORK',
      ok: true,
      index: 0
    }
  },
  methods: {
    onClickImage (value) {
      this.ok=false;
      this.index=value;
      console.log(this.index);
    },
    onClickBack (value) {
      this.ok=true;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#title {
  text-align: center;
  font-size: 14px;
  letter-spacing: 3px;
  color: #ffffff;
  margin: 50px auto 55px;
}

</style>
