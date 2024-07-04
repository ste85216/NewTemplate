<template>
  <v-container id="sectionOne" class="mt-8">
    <v-row>
      <v-col cols="12">
        <v-img id="volleyball" src="../assets/volleyball.png" @load="animate"></v-img>
        <v-img id="girl" src="../assets/volleyball-girl.png"></v-img>
      </v-col>
      <v-col cols="12">
        <h2>Do you want to be a professional volleyball player?</h2>
        <p>We offer training in a variety of difficulty levels that volleyball players of all skill levels can enjoy. You will learn volleyball from professionals with our competent and experienced staff.</p>
        <v-img class="divider" src="../assets/divider.jpg"></v-img>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { onMounted, nextTick } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import AOS from 'aos'

  AOS.init()

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
      rotation: 360,
      duration: 15,
      repeat: -1,
      repeatDelay: 0,
      ease: 'none',
    }, 0)
    .fromTo(girlEl, {
      x: -600, // 初始位置在屏幕外
    }, {
      x: 60,
      delay: 0.5,
      duration: 1,
      repeat: 0,
      ease: 'bounce',
    }, 0) // 0 确保同时开始
  }

onMounted(async () => {
  await nextTick(); // 確保DOM已經渲染完成
  animateVolleyball(); // 仅在挂载后调用以检查是否能找到元素
});

</script>

<style scoped lang="scss">
#girl {
  width: px;
  left: 5%;
}

#volleyball {
  width: 780px;
  position: absolute;
}
.v-col h2 {
  background: linear-gradient(90deg, rgb(37, 111, 187), rgb(237, 196, 83) );
  background-clip: text;
  color: transparent;
  font-family: "Satoshi Black";
  font-size: 30px;
  font-weight: 900;
}

.divider {
  width: 120px;
}
</style>
