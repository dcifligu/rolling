<script setup>
import Circles from './components/Circles.svg.vue'
</script>

<template>
  <div class="bg-[#F6F6F6] bg-noise h-screen w-screen relative z-10 overflow-hidden">
    <Circles class="absolute z-20"/>
    <div class="h-full w-full relative z-30">
      <div class="p-8 w-full h-full">
        <div class="flex w-full h-full items-end">
          <div class="bg-black w-1/4 h-fit p-2 rounded-full">
            <div class="flex h-fit w-full items-center justify-between">
              <div class="bg-white w-24 h-24 rounded-full"></div>
              <div class="w-fit pr-4 h-fit flex flex-col items-center justify-center">
                <span class="text-white text-4xl font-light uppercase">Click here</span>
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
  background-image: url("./assets/media/noise.png");
  background-size: auto;
  background-repeat: repeat;
  background-blend-mode: multiply;
}

</style>
