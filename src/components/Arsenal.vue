<template>

  <div id="arsenal">

    <p id="title">{{ title }}</p>

    <div class="images-block d-flex flex-lg-row">
      <div class="p-2" v-for="gadgets in arsenal"><img :src="gadgets.path"/></div>
    </div>

  </div>

</template>

<script>
export default {
  data () {
    return {
      title: 'ARSENAL',
      arsenal: [
        { path: require('../assets/batplane.png') },
        { path: require('../assets/batmobile.png') },
        { path: require('../assets/batpod.png') },
        { path: require('../assets/batclaw.png') },
        { path: require('../assets/batarang.png') },
        { path: require('../assets/batarmor.png') }
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#arsenal{
  background-color: #caced0;
  padding-bottom: 50px;
}

#title {
  text-align: center;
  font-size: 14px;
  font-weight: bold;
  letter-spacing: 3px;
  color: #131f22;
  padding-top: 50px;
  margin-bottom: 0px;
}

.images-block {
  margin: auto auto;
  max-width: 1280px;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

img {
  height: 225px;
  width: 225px;
  margin: 20px 50px;
}
</style>
