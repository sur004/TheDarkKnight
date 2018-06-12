<template>

  <div id="people">
    <p id="title">{{ title }}</p>
    <div class="mobile-navigation">
      <span :class="{'mobile-active-client' : (index == 0)}" @click="activate(people[0].id)"></span>
      <span :class="{'mobile-active-client' : (index == 1)}" @click="activate(people[1].id)"></span>
      <span :class="{'mobile-active-client' : (index == 2)}" @click="activate(people[2].id)"></span>
      <span :class="{'mobile-active-client' : (index == 3)}" @click="activate(people[3].id)"></span>
      <span :class="{'mobile-active-client' : (index == 4)}" @click="activate(people[4].id)"></span>
      <span :class="{'mobile-active-client' : (index == 5)}" @click="activate(people[5].id)"></span>
    </div>
    <div class="people-slider d-flex flex-lg-row" :class="{'animation-target' : (people[index].active == true)}">

      <div class="people-pics">
        <div class="people-pic" :style="{ 'background-image': 'url(' +people[index].path+')'}"></div>
        <p class="people-name">{{ people[index].name }}</p>
        <p class="people-title">{{ people[index].title }}</p>
      </div>

      <div class="people-messages">
        <p class="quote">{{ people[index].message }}</p>
      </div>

    </div>

    <div class="people-controls d-flex flex-lg-row">
      <div @click="prev" class="prev-wrapper"><i class="fas fa-chevron-left left-control"></i></div>
      <div @click="next" class="next-wrapper"><i class="fas fa-chevron-right right-control"></i></div>
    </div>

    <div class="logos d-flex flex-lg-row">
      <img v-for="logo in people" :class="{'logo':(index != logo.id), 'active':(index === logo.id)}" @click="activate(logo.id)" :src="logo.logo"/>
    </div>

  </div>

</template>

<script>
export default {
  data () {
    return {
      title: 'PEOPLE',
      index: 0,
      people: [
        {active: false, id: 0, path: require('../assets/Superman.png'), name: 'SUPERMAN', title: 'Man of Steel', message: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod  et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis ae dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.', logo: require('../assets/Super.svg')},
        {active: false, id: 1, path: require('../assets/WonderWoman.png'), name: 'WONDER WOMAN', title: 'Princess of Themyscira', message: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis audolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.', logo: require('../assets/Wonder.svg')},
        {active: false, id: 2, path: require('../assets/TheFlash.png'), name: 'FLASH', title: 'Scarlet Speedster', message: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.', logo: require('../assets/Flash.svg')},
        {active: false, id: 3, path: require('../assets/GreenLantern.png'), name: 'GREEN LANTERN', title: 'Emerald Warrior', message: 'Lorem ipsum dolor sit amet, consectetur adip tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Dui irure reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.', logo: require('../assets/Lantern.svg')},
        {active: false, id: 4, path: require('../assets/Hawkgirl.png'), name: 'HAWKGIRL', title: 'Thanagarian Warrior', message: 'Lorem ipsum dolor sit amet, consectetur adipisicint ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis auteor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.', logo: require('../assets/Hawk.svg')},
        {active: false, id: 5, path: require('../assets/MartianManhunter.png'), name: 'MARTIAN MANHUNTER', title: 'Last Surviving Martian', message: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrude dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.', logo: require('../assets/Martian.svg')}
      ]
    }
  },
  methods: {
    prev() {
      //console.log(this.people[this.index].id);
      if( this.index == 0 ) {
        this.index = this.people.length-1;
        var self = this;
        self.people[self.index].active = true;
        setTimeout(function(){ self.people[self.index].active = false; }, 750);
      }
      else {
        this.index--;
        var self = this;
        self.people[self.index].active = true;
        setTimeout(function(){ self.people[self.index].active = false; }, 750);
      }
    },
    next() {
      //console.log(this.people[this.index].id);
      if( this.index == 5 ) {
        this.index = 0;
        var self = this;
        self.people[self.index].active = true;
        setTimeout(function(){ self.people[self.index].active = false; }, 750);
      }
      else {
        this.index++;
        var self = this;
        self.people[self.index].active = true;
        console.log(self.people[self.index])
        setTimeout(function(){ self.people[self.index].active = false; }, 750);
      }
    },
    activate(identity) {
      this.index = identity;
      var self = this;
      self.people[self.index].active = true;
      setTimeout(function(){ self.people[self.index].active = false; }, 750);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#people{
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
  margin-bottom: 30px;
}

.mobile-navigation {
  max-width: 400px;
  margin: 0px auto;
  text-align: center;
  height: 20px;
  display: flex;
  justify-content: space-between;
  display: none;
}

span {
  height: 16px;
  width: 16px;
  border-radius: 50%;
  border-style: solid;
  border-color: rgb(0, 0, 0);
  opacity: 0.3;
  display: inline-block;
}

.people-controls {
  position: absolute;
  width: 100%;
  height: 100%;
}

.prev-wrapper {
  margin: -100px auto 0px 40px;
}

.left-control {
  color: #131f22;
  opacity: 0.7;
  height: 35px;
  width: 35px;
  margin: -100px auto 0px 40px;
}

.left-control:hover {
  cursor: pointer;
  opacity: 1;
  transition: 0.3s;
}

.next-wrapper {
  margin: -100px 40px 0px auto;
}

.right-control {
  color: #131f22;
  opacity: 0.7;
  height: 35px;
  width: 35px;
  margin: -100px 40px 0px auto;
}

.right-control:hover {
  cursor: pointer;
  opacity: 1;
  transition: 0.3s;
}

.people-slider {
  max-width: 1280px;
  height: 300px;
  margin: 0px auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  transition: fade .5s;
}

.people-pics {
    max-width: 300px;
    width: 300px;
}

.people-pic {
  background-size: 145%;
  background-repeat: no-repeat;
  background-position: top center;
  border-radius: 50%;
  height: 100px;
  width: 100px;
  margin: 60px auto 0px;
  display: block;
}

.people-name{
  font-size: 12px;
  margin: 20px auto 0px;
  text-align: center;
  font-weight: bold;
  letter-spacing: 2px;
}

.people-title {
  font-size: 11px;
  text-align: center;
  letter-spacing: 2px;
  margin: 5px 0px;
}

.people-messages {
  max-width: 500px;
  width: 400px;
  margin: 50px 20px;
}

.quote {
  font-size: 16px;
  line-height: 30px;
  letter-spacing: 2px;
}

.logos {
  max-width: 1200px;
  display: flex;
  flex-wrap: wrap;
  margin: 20px auto;
  justify-content: center;
}
.logo {
  height: 100px;
  width: 100px;
  opacity: 0.3;
  background-position: center;
  background-size: 125%;
  background-repeat: no-repeat;
  margin: 50px;
}

.logo:hover {
  cursor: pointer;
}

.active {
  height: 100px;
  width: 100px;
  margin: 50px;
  opacity: 0.7;
  transform: scale(1.3);
  transition: 0.5s;
}

.animation-target {
  -webkit-animation: animation 750ms linear both;
  animation: animation 750ms linear both;
}

/* Generated with Bounce.js. Edit at https://goo.gl/MMDwjm */

@-webkit-keyframes animation {
  0% { -webkit-transform: matrix3d(0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  3.2% { -webkit-transform: matrix3d(0.345, 0.098, 0, 0, 0.065, 0.345, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0.345, 0.098, 0, 0, 0.065, 0.345, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  4.5% { -webkit-transform: matrix3d(0.485, 0.163, 0, 0, 0.107, 0.485, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0.485, 0.163, 0, 0, 0.107, 0.485, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  6.41% { -webkit-transform: matrix3d(0.673, 0.242, 0, 0, 0.158, 0.673, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0.673, 0.242, 0, 0, 0.158, 0.673, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  9.01% { -webkit-transform: matrix3d(0.88, 0.288, 0, 0, 0.188, 0.88, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0.88, 0.288, 0, 0, 0.188, 0.88, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  12.71% { -webkit-transform: matrix3d(1.064, 0.241, 0, 0, 0.159, 1.064, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.064, 0.241, 0, 0, 0.159, 1.064, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  13.51% { -webkit-transform: matrix3d(1.087, 0.221, 0, 0, 0.146, 1.087, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.087, 0.221, 0, 0, 0.146, 1.087, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  17.92% { -webkit-transform: matrix3d(1.139, 0.105, 0, 0, 0.07, 1.139, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.139, 0.105, 0, 0, 0.07, 1.139, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  18.92% { -webkit-transform: matrix3d(1.137, 0.082, 0, 0, 0.055, 1.137, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.137, 0.082, 0, 0, 0.055, 1.137, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  25.23% { -webkit-transform: matrix3d(1.075, -0.001, 0, 0, -0.001, 1.075, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.075, -0.001, 0, 0, -0.001, 1.075, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  29.03% { -webkit-transform: matrix3d(1.032, -0.015, 0, 0, -0.01, 1.032, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.032, -0.015, 0, 0, -0.01, 1.032, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  31.43% { -webkit-transform: matrix3d(1.012, -0.017, 0, 0, -0.011, 1.012, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.012, -0.017, 0, 0, -0.011, 1.012, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  34.63% { -webkit-transform: matrix3d(0.994, -0.014, 0, 0, -0.01, 0.994, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0.994, -0.014, 0, 0, -0.01, 0.994, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  40.14% { -webkit-transform: matrix3d(0.985, -0.007, 0, 0, -0.005, 0.985, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0.985, -0.007, 0, 0, -0.005, 0.985, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  56.46% { -webkit-transform: matrix3d(1, 0.001, 0, 0, 0.001, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1, 0.001, 0, 0, 0.001, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  62.36% { -webkit-transform: matrix3d(1.002, 0.001, 0, 0, 0, 1.002, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.002, 0.001, 0, 0, 0, 1.002, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  81.48% { -webkit-transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  84.68% { -webkit-transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  100% { -webkit-transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
}

@keyframes animation {
  0% { -webkit-transform: matrix3d(0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  3.2% { -webkit-transform: matrix3d(0.345, 0.098, 0, 0, 0.065, 0.345, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0.345, 0.098, 0, 0, 0.065, 0.345, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  4.5% { -webkit-transform: matrix3d(0.485, 0.163, 0, 0, 0.107, 0.485, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0.485, 0.163, 0, 0, 0.107, 0.485, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  6.41% { -webkit-transform: matrix3d(0.673, 0.242, 0, 0, 0.158, 0.673, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0.673, 0.242, 0, 0, 0.158, 0.673, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  9.01% { -webkit-transform: matrix3d(0.88, 0.288, 0, 0, 0.188, 0.88, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0.88, 0.288, 0, 0, 0.188, 0.88, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  12.71% { -webkit-transform: matrix3d(1.064, 0.241, 0, 0, 0.159, 1.064, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.064, 0.241, 0, 0, 0.159, 1.064, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  13.51% { -webkit-transform: matrix3d(1.087, 0.221, 0, 0, 0.146, 1.087, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.087, 0.221, 0, 0, 0.146, 1.087, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  17.92% { -webkit-transform: matrix3d(1.139, 0.105, 0, 0, 0.07, 1.139, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.139, 0.105, 0, 0, 0.07, 1.139, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  18.92% { -webkit-transform: matrix3d(1.137, 0.082, 0, 0, 0.055, 1.137, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.137, 0.082, 0, 0, 0.055, 1.137, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  25.23% { -webkit-transform: matrix3d(1.075, -0.001, 0, 0, -0.001, 1.075, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.075, -0.001, 0, 0, -0.001, 1.075, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  29.03% { -webkit-transform: matrix3d(1.032, -0.015, 0, 0, -0.01, 1.032, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.032, -0.015, 0, 0, -0.01, 1.032, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  31.43% { -webkit-transform: matrix3d(1.012, -0.017, 0, 0, -0.011, 1.012, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.012, -0.017, 0, 0, -0.011, 1.012, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  34.63% { -webkit-transform: matrix3d(0.994, -0.014, 0, 0, -0.01, 0.994, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0.994, -0.014, 0, 0, -0.01, 0.994, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  40.14% { -webkit-transform: matrix3d(0.985, -0.007, 0, 0, -0.005, 0.985, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(0.985, -0.007, 0, 0, -0.005, 0.985, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  56.46% { -webkit-transform: matrix3d(1, 0.001, 0, 0, 0.001, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1, 0.001, 0, 0, 0.001, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  62.36% { -webkit-transform: matrix3d(1.002, 0.001, 0, 0, 0, 1.002, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1.002, 0.001, 0, 0, 0, 1.002, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  81.48% { -webkit-transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  84.68% { -webkit-transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
  100% { -webkit-transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
}

@media (max-width: 1024px) {
  .mobile-navigation {
    display: block;
  }

  span:hover {
    cursor: pointer;
  }

  .active {
    display: none;
  }

  .logo {
    display: none;
  }

  .left-control, .right-control, .people-controls {
    height: 0px;
    display: none
  }

  .mobile-active-client {
      opacity: 0.7;
  }
}

@media (max-width: 760px) {
  #people {
    height: 800px;
  }
}







</style>
