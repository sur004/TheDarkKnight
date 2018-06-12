<template>

  <div class="home">

    <header :style="{ 'background-image': 'url(' + backImage + ')' }">
      <nav id="mynav" class="navbar navbar-expand-lg navbar-dark fixed-top" :class="{ 'scroll-active': scrolled==true, 'ham-expand': hamExpand==true}">

        <a class="navbar-brand" href="#"><img class="logo" :src="navbarLogo"/></a>

        <button class="navbar-toggler" type="button" data-toggle="collapse" @click="hamburger" data-target="#navbarSupportedContent">
          <i class="fas fa-bars"></i>
        </button>

        <div class="nav-links-block collapse navbar-collapse" id="navbarSupportedContent">

          <ul class="navbar-nav ml-auto">
            <li class="nav-item" v-for="navlink in navbarLinks"><a class="nav-link" v-smooth-scroll="{ duration: 1000, offset: -70 }" v-bind:href="navlink.href">{{ navlink.navlink }}</a></li>
          </ul>

        </div>

      </nav>
      <div class="header-block">

        <h1>{{ mainText }}</h1>
        <p>{{ message }}</p>

        <div class="head-buttons">
          <a class="headlinks" v-for="headlink in headerLinks" v-smooth-scroll="{ duration: 1000, offset: -70 }" v-bind:href="headlink.href">{{ headlink.headlink }}</a>
        </div>

      </div

    </header>

  </div>

</template>

<script>
import About from './About.vue'
export default {
  name: 'Header',
  data () {
    return {
      scrolled: false,
      hamExpand: false,
      backImage: require('../assets/header.jpg'),
      navbarLinks: [
        {navlink: 'ABOUT', href: '#about'},
        {navlink: 'ARSENAL', href: '#arsenal'},
        {navlink: 'WORK', href: '#work'},
        {navlink: 'PEOPLE', href: '#people'},
        {navlink: 'CONTACT', href: '#contact'}
      ],
      navbarLogo: require('../assets/Navbar-logo.svg'),
      mainText: 'THE DARK KNIGHT',
      message: 'DETECTIVE // MARTIAL ARTIST // TACTICIAN',
      headerLinks: [
        {headlink: 'MY WORK', href: '#work'},
        {headlink: 'MY SKILLS', href: '#arsenal'}
      ]
    }
  },
  methods: {
    handleScroll () {
      if( window.scrollY > 500 )
        this.scrolled = true;
      else if( window.scrollY < 500 )
        this.scrolled = false;
    },
    hamburger() {
      this.hamExpand = !this.hamExpand;
    }
  },
  created () {
    window.addEventListener('scroll', this.handleScroll);
  },
  destroyed () {
    window.removeEventListener('scroll', this.handleScroll);
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.home {
  margin: 0px 0px;
}
header {
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  height: 100vh;
  width: 100%;
}

.ham-expand {
  background-color: rgba(38, 55, 60, 0.8);
  transition: 0.5s;
}

nav {
  border-style: solid !important;
  border-bottom-color: rgba(255, 255, 255, 0.5);
  border-top: none !important;
  border-left: none !important;
  border-right: none !important;
  border-width: thin !important;
  padding: 0px 0px !important;
  background-color: rgba(38, 55, 60, 0.0);
}

.logo {
  height: 45px;
  width: 120px;
  margin: 10px auto 0px 50px;
  padding: 0px 0px !important;

}

button {
  margin: 0px 50px 0px auto;
  padding: 0px 0px !important;
  color: #ffffff !important;
  border: none !important;
}

.nav-links-block {
  margin-right: 50px;
}

.nav-item {
  display: inline-block;
  margin: 15px 25px 10px;
}

.nav-link {
  color: rgba(255, 255, 255, 1) !important;
  font-weight: 600;
  font-size: 10px;
  letter-spacing: 2px;
}

.nav-link:hover {
  color: rgba(255, 255, 255, 0.7) !important;
  transition: all 0.3s;
}

.header-block {
    padding: 20% 10%;
}

.scroll-active {
  background-color: rgba(38, 55, 60, 0.8);
  transition: 0.5s;
}

h1 {
  color: #ffffff;
  text-align: center;
  font-size: 320%;
  line-height: 150%;
  letter-spacing: 15px;
}

p {
  font-size: 75%;
  color: #ffffff;
  text-align: center;
  letter-spacing: 5px;
}
.head-buttons {
  padding-top: 30px;
  letter-spacing: 2px;
  text-align: center;
}
.headlinks {
  border-style: solid;
  border-width: thin;
  border-color: rgb(255, 255, 255);
  background-color: rgba(0, 0, 0, 0.5);
  border-radius: 2px;
  padding: 10px 20px;
  display: inline-block;
  margin: 10px 20px;
  color: #ffffff;
  font-weight: 600;
  font-size: 10px;
  text-decoration: none;
}

.headlinks:hover {
  background-color: #ffffff;
  color: #191d1f;
  transition: all 0.3s;
}

@media (max-width: 600px) {
  h1 {
    padding-top: 75px;
    font-size: 45px;
  }

  p {
    font-size: 10px;
  }
}
</style>
