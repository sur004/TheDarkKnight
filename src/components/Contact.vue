<template>

  <div id="contact">
    <p id="title">{{ title }}</p>
    <p id="message">{{ message }}</p>

    <div class="social d-flex flex-lg-row">
      <a class="soc-icons" v-for="icons in faClass" :href="icons.href">
        <i :class="icons.path"></i>
      </a>
    </div>

    <hr>

    <footer>Written and coded by Suraj S</footer>
  </div>

</template>

<script>

export default {
  data () {
    return {
      title: 'CONTACT',
      message: 'USE THE BAT SIGNAL',
      faClass: [
        {path: 'soc fab fa-twitter', href: 'https://twitter.com'},
        {path: 'soc fab fa-facebook-f', href: 'https://facebook.com'},
        {path: 'soc fab fa-instagram', href: 'https://instagram.com'}
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#contact {
  background-color: #293a3f;
}

#title {
  text-align: center;
  font-size: 14px;
  letter-spacing: 3px;
  color: #ffffff;
  margin: 50px auto;
}

#message {
  color: #ffffff;
  font-size: 400%;
  margin: 100px auto;
  text-align: center;
  line-height: 150%;
  letter-spacing: 5px;
}

.social {
  width: 320px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin: 0px auto 50px;
}

.soc-icons {
  margin: 0px 3%;
}

.soc {
  height: 25px;
  width: 25px;
  color: #ffffff;
}

.soc:hover {
  transition: .3s;
  transform: scale(1.2);
}

hr {
  border-color: rgba(255, 255, 255, 0.5);
  border-width: thin;
}
footer {
  text-align: center;
  color: #ffffff;
  letter-spacing: 3px;
  font-size: 10px;
  margin-bottom: 10px;
}
</style>
