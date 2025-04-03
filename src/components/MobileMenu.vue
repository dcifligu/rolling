<script setup>
import { onMounted } from "vue";
import gsap from "gsap";
import ColorWheel from "./ColorWheel.svg.vue";

onMounted(() => {
    const circles = gsap.utils.toArray(".grid div .blend"); 
    const gridSize = 10; 
    const delayFactor = 0.05; 

    const getCoords = (index) => ({
        x: index % gridSize,
        y: Math.floor(index / gridSize),
    });

    const topRightIndex = gridSize - 1;
    const topRightCoords = getCoords(topRightIndex);

    const tl = gsap.timeline();

    circles.forEach((circle, index) => {
        const coords = getCoords(index);

        const distance = Math.abs(coords.x - topRightCoords.x) + Math.abs(coords.y - topRightCoords.y);

        tl.to(circle, {
            scale: 5,
            opacity: 1,
            duration: 0.8,
            repeat: -1,
            yoyo: true,
            ease: "power2.out",
            delay: distance * delayFactor,
        }, 0);
    });
});
</script>

<template>
    <div class="h-screen w-screen text-[#393B45] bg-[#DAE0D2] overflow-hidden">
        <div class="w-full h-full p-6">
            <div class="w-full h-full">
                <div class="grid h-3/5 grid-cols-10 grid-rows-10 gap-4">
                    <div v-for="i in 100" 
                    :key="i" 
                    class="w-full h-full flex justify-center items-center">
                        <ColorWheel />
                    </div>
                </div>
                <div class="my-2 py-3">
                    <div class="w-full h-1/5 flex items-center">
                        <h1 class="text-4xl font-bold text-[#393B45]">Mobile</h1>
                    </div>
                    <div class="w-full h-1/5 flex items-center">
                        <h2 class="text-2xl font-bold text-[#393B45]">Nothing ever happens</h2>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
