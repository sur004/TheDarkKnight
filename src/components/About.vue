<template>

  <div id="about">
    <p id="title">{{ title }}</p>
    <div id="aboutPic" :style="{ 'background-image': 'url(' +aboutPic+ ')'}"></div>
    <p id="message">{{ message }}</p>
  </div>

</template>

<script>

export default {
  data () {
    return {
      title: 'ABOUT MYSELF',
      aboutPic: require('../assets/About.jpg'),
      message: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#about {
  background-color: #293a3f;
}

#title {
  text-align: center;
  font-size: 14px;
  letter-spacing: 3px;
  color: #ffffff;
  margin: 50px auto;
}

#aboutPic {
  background-size: cover;
  background-position: center;
  height: 150px;
  width: 150px;
  border-radius: 50%;
  border-style: solid;
  border-color: #0e1416;
  border-width: thick;
  display: block;
  margin: 20px auto;
}

#message {
  max-width: 400px;
  color: #ffffff;
  font-size: 14px;
  margin: 40px auto 100px;
  text-align: center;
  line-height: 40px;
  letter-spacing: 3px;
}
</style>
