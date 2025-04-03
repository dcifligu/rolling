<script setup>
import Circles from './Circles.svg.vue'
import gsap from 'gsap'


function change_color() {
  
  document.getElementById('main_bg').classList.add('bg-noise-w');
  document.getElementById('main_bg').classList.remove('bg-noise');
  document.getElementById('maintxt').style.color = '#F6F6F6';
  document.querySelectorAll('circle[id^="circle_"][id$="_dot"]').forEach(circle => {
    circle.setAttribute("fill", "#F6F6F6");
  });    
    
  //gsap animation
    gsap.to("#circle", { x: 320, duration: 0.8, ease: "power2.inOut" });

    gsap.to("#buttontxt", { x: -100, duration: 0.8, ease: "power2.inOut" });

    gsap.to("#buttontxt", { opacity: 0, duration: 0.25, onComplete: function() {
        document.getElementById("buttontxt").innerHTML = "Discover More";
        gsap.to("#buttontxt", { opacity: 1, duration: 0.25 });
    }});

    gsap.to("#button", { backgroundColor: "#F6F6F6", duration: 0.5 });
    gsap.to("#circle", { backgroundColor: "#1E1E1E", duration: 0.5 });
    gsap.to("#buttontxt", { color: "#1E1E1E", duration: 0.5 });
}

</script>

<template>
  <div id="main_bg" class="bg-[#F6F6F6] bg-noise h-screen w-screen relative z-10 overflow-hidden duration-300 transition-all">
    <Circles class="absolute z-0"/>
    <div class="absolute z-20 w-full h-full flex items-center justify-center">
      <h1 id="maintxt" class="text-9xl text-center font-bold montserrat tracking-wider uppercase">
        Lorem ipsum
        <br>
        Dummy text
        <br>
        Filler
      </h1>
    </div>
    <div class="h-full w-full relative z-30">
      <div class="p-8 w-full h-full">
        <div class="flex w-full h-full items-end">
          <div id="button" class="bg-[#1E1E1E] w-fit h-fit p-2 rounded-full cursor-pointer" @click="change_color()">
            <div class="flex gap-6 h-fit w-full items-center justify-between">
              <div id="circle" class="bg-white w-24 h-24 rounded-full"></div>
              <div class="w-fit pr-6 h-fit flex flex-col items-center justify-center">
                <span id="buttontxt" class="text-white text-3xl font-thin montserrat tracking-wide uppercase">Learn <br> more about us</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.bg-noise {
  background-image: url('../assets/media/img-noise-200x200.png');
  background-repeat: repeat;
  background-blend-mode: multiply;
}

.bg-noise-w {
  background-image: url('../assets/media/img-noise-200x200W.png');
  background-repeat: repeat;
  background-blend-mode: multiply;
}

.montserrat {
  font-family: "Montserrat", sans-serif;
  font-optical-sizing: auto;
}

</style>
