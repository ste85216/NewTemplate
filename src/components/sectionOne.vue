<template>
  <v-container id="sectionOne" class="mt-8" >
    <v-row>
      <v-col xl="2"></v-col>
      <v-col cols="12" md="7" xl="5">
        <v-img id="volleyball" src="../assets/volleyball.png" @load="animate"></v-img>
        <v-img id="girl" src="../assets/volleyball-girl.png"></v-img>
      </v-col>
      <v-col></v-col>
      <v-col id="left" cols="12" md="4" xl="3">
        <h2 data-aos="fade-up" data-aos-duration="2000">Do you want to be a professional volleyball player?</h2>
        <p data-aos="fade-up" data-aos-duration="2000">We offer training in a variety of difficulty levels that volleyball players of all skill levels can enjoy. You will learn volleyball from professionals with our competent and experienced staff.</p>
        <v-img class="divider" src="../assets/divider.jpg" data-aos="fade-up" data-aos-duration="2000"></v-img>
        <v-container class="mt-5">
          <v-row class="d-flex flex-column">
            <v-col data-aos="fade-up" data-aos-duration="2000">
              <v-row >
                <v-col cols="2" >
                  <v-img class="medal" src="../assets/kindpng_2988353.png"></v-img>
                </v-col>
                <v-col>
                  <h3>Professional Team</h3>
                  <p class="mt-3">We make you professional by adding your sincerity as well as professionalism.</p>
                </v-col>
              </v-row>
            </v-col>
            <v-col data-aos="fade-up" data-aos-duration="2000">
              <v-row>
                <v-col cols="2">
                  <v-img class="medal" src="../assets/kindpng_2988353.png"></v-img>
                </v-col>
                <v-col>
                  <h3>Professional Trainings</h3>
                  <p class="mt-3">We always travel with the best equipment, respecting people and the environment.

</p>
                </v-col>
              </v-row>
            </v-col>
            <v-col class="btn mt-3" data-aos="fade-up" data-aos-duration="2000">
              <v-btn>Get to know us → </v-btn>
            </v-col>
          </v-row>
        </v-container>
      </v-col>
      <v-col xl="1"></v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { onMounted, nextTick } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import AOS from 'aos'
import 'aos/dist/aos.css';

gsap.registerPlugin(ScrollTrigger) 

const animate = () => {
  const volleyballEl = document.querySelector('#volleyball');
  const girlEl = document.querySelector('#girl')
    
  let tl = gsap.timeline({
    scrollTrigger: {
      trigger: '#sectionOne',
      start: 'top bottom',
      end: 'top center',
      // markers: true
    }
  })

  tl
    .fromTo(volleyballEl, {
      x: -600,
    }, {
      x: -50,
      duration:1,
      ease: 'power1.inOut',
    })
    .to(volleyballEl, {
      rotation: 720,
      duration: 30,
      repeat: -1,
      repeatDelay: 0,
      ease: 'none',
    }, 0)
    .fromTo(girlEl, {
      x: -600, // 初始位置在屏幕外
    }, {
      x: 60,
      delay: 0.5,
      duration: 1.5,
      repeat: 0,
      ease: 'bounce',
    }, 0) // 0 确保同时开始
  }

onMounted(async () => {
  await nextTick(); // 確保DOM已經渲染完成
  animate(); // 仅在挂载后调用以检查是否能找到元素
});

AOS.init({
  once:true,


})

</script>

<style scoped lang="scss">
@import '../styles/settings.scss';

#girl {
  width: 500px;
  left: 5%;
}

#volleyball {
  width: 600px;
  position: absolute;
}
h2 {
  background: linear-gradient(90deg, rgb(37, 111, 187), rgb(237, 196, 83) );
  background-clip: text;
  color: transparent;
  font-family: "Satoshi Black";
  font-size: 32px;
  font-weight: 900;
}

.divider {
  width: 120px;
}

.medal {
  width: 50px;
  transition: 1s;
  &:hover {
    filter: hue-rotate(120deg);
  }
}

.btn .v-btn {
  width: 100%;
  height: 70px;
  background: #256fbb;
  color: #fff;
  font-family: "Satoshi Black";
  font-weight: bold;
  border-radius: 50px;
  transition: 1s;
  &:hover {
    background: #edc453;
  }
}

@include md {
  #girl {
    width: 600px;
  }

  #volleyball {
    width: 650px;
  }

  #left {
    margin-top: 5%;
  }

  .btn .v-btn {
    width: 240px;
    height: 70px;
  }
}

@include xl {
  #girl {
    width: 750px;
  }

  #volleyball {
    width: 850px;
  }

  h2 {
    font-size: 34px;
  }
}
</style>
