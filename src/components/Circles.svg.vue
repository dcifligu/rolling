<script setup>
import { onMounted } from 'vue';
import gsap from 'gsap';
import { MotionPathPlugin } from 'gsap/MotionPathPlugin';

gsap.registerPlugin(MotionPathPlugin);

onMounted(() => {
  const circles = [1, 2, 3, 4, 5];
  const reverseCircles = [2, 5, 4]; 

  circles.forEach(num => {
    gsap.to(`#circle_${num}_dot`, {
      duration: 5, 
      repeat: -1, 
      ease: "none", 
      motionPath: {
        path: `#circle_${num}_inner_path`, 
        align: `#circle_${num}_inner_path`,
        autoRotate: true,
        alignOrigin: [0.5, 0.5],
        start: reverseCircles.includes(num) ? 1 : 0, 
        end: reverseCircles.includes(num) ? 0 : 1
      }
    });
  });
});
</script>


<template>

    <svg width="1920" height="1080" viewBox="0 0 1920 1080" fill="none" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="circleGradient" cx="50%" cy="50%" r="50%">
            <stop offset="0%" stop-color="rgba(0,212,255,1)" />
            <stop offset="100%" stop-color="rgba(2,0,36,1)" />
          </radialGradient>
        </defs>

        <!-- Circle 1 -->
        <path id="circle_1_stroke" d="M1100 264.5C1100 456.408 943.534 612 750.5 612C557.466 612 401 456.408 401 264.5C401 72.5918 557.466 -83 750.5 -83C943.534 -83 1100 72.5918 1100 264.5Z" stroke="#B2B2B2" stroke-width="4"/>
        <path id="circle_1_inner_path" d="M1070 264.5C1070 436 930 572 750.5 572C571 572 431 436 431 264.5C431 93 571 -43 750.5 -43C930 -43 1070 93 1070 264.5Z" fill="none" stroke="none"/>
        <circle id="circle_1_dot" cx="500.5" cy="473.5" r="7.5" fill="#1E1E1E"/>

        <!-- Circle 2 -->
        <path id="circle_2_stroke" d="M2077 332C2077 600.399 1858.08 818 1588 818C1317.92 818 1099 600.399 1099 332C1099 63.6012 1317.92 -154 1588 -154C1858.08 -154 2077 63.6012 2077 332Z" stroke="#B2B2B2" stroke-width="4"/>
        <path id="circle_2_inner_path" d="M2047 332C2047 570 1838 788 1588 788C1338 788 1129 570 1129 332C1129 94 1338 -124 1588 -124C1838 -124 2047 94 2047 332Z" fill="none" stroke="none"/>
        <circle id="circle_2_dot" cx="1136.5" cy="272.5" r="7.5" fill="#1E1E1E"/>

        <!-- Circle 3 -->
        <path id="circle_3_stroke" d="M1127 963.5C1127 1155.38 968.323 1311 772.5 1311C576.677 1311 418 1155.38 418 963.5C418 771.618 576.677 616 772.5 616C968.323 616 1127 771.618 1127 963.5Z" stroke="#B2B2B2" stroke-width="4"/>
        <path id="circle_3_inner_path" d="M1097 963.5C1097 1135 947 1272 772.5 1272C598 1272 448 1135 448 963.5C448 792 598 655 772.5 655C947 655 1097 792 1097 963.5Z" fill="none" stroke="none"/>
        <circle id="circle_3_dot" cx="1104.5" cy="993.5" r="7.5" fill="#1E1E1E"/>

        <!-- Circle 4 -->
        <path id="circle_4_stroke" d="M438 800.5C438 992.382 279.323 1148 83.5 1148C-112.323 1148 -271 992.382 -271 800.5C-271 608.618 -112.323 453 83.5 453C279.323 453 438 608.618 438 800.5Z" stroke="#B2B2B2" stroke-width="4"/>
        <path id="circle_4_inner_path" d="M408 800.5C408 962 268 1108 83.5 1108C-101 1108 -241 962 -241 800.5C-241 639 -101 493 83.5 493C268 493 408 639 408 800.5Z" fill="none" stroke="none"/>
        <circle id="circle_4_dot" cx="229.5" cy="519.5" r="7.5" fill="#1E1E1E"/>

        <!-- Circle 5 -->
        <path id="circle_5_stroke" d="M414 101.5C414 293.382 255.323 449 59.5 449C-136.323 449 -295 293.382 -295 101.5C-295 -90.3817 -136.323 -246 59.5 -246C255.323 -246 414 -90.3817 414 101.5Z" stroke="#B2B2B2" stroke-width="4"/>
        <path id="circle_5_inner_path" d="M384 101.5C384 264 234 419 59.5 419C-115 419 -265 264 -265 101.5C-265 -61 -115 -216 59.5 -216C234 -216 384 -61 384 101.5Z" fill="none" stroke="none"/>
        <circle id="circle_5_dot" cx="290.5" cy="339.5" r="7.5" fill="#1E1E1E"/>

        <!-- Circle 6 -->
        <path id="circle_6_stroke" d="M1808 1154.5C1808 1346.38 1649.32 1502 1453.5 1502C1257.68 1502 1099 1346.38 1099 1154.5C1099 962.618 1257.68 807 1453.5 807C1649.32 807 1808 962.618 1808 1154.5Z" stroke="#B2B2B2" stroke-width="4"/>
        </svg>
           
</template>