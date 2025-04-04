<script setup>
import { onMounted } from "vue";
import gsap from "gsap";
import ColorWheel from "./ColorWheel.svg.vue";

onMounted(() => {
    const circles = gsap.utils.toArray(".grid div .blend"); 
    const gridSize = 31; 
    const delayFactor = 0.055; 

    const getCoords = (index) => ({
        x: index % gridSize,
        y: Math.floor(index / gridSize),
    });

    const getIndex = (x, y) => y * gridSize + x;

    const getAdjacentNodes = (index) => {
        const { x, y } = getCoords(index);
        let adjacent = [];

        if (x > 0) adjacent.push(getIndex(x - 1, y));  
        if (x < gridSize - 1) adjacent.push(getIndex(x + 1, y)); 
        if (y > 0) adjacent.push(getIndex(x, y - 1));
        if (y < gridSize - 1) adjacent.push(getIndex(x, y + 1));

        return adjacent;
    };

    const topRightIndex = gridSize - 1; 
    
    let visited = new Set();
    let queue = [{ index: topRightIndex, delay: 0 }];
    let animationOrder = [];

    while (queue.length > 0) {
        let { index, delay } = queue.shift();
        if (visited.has(index)) continue;

        visited.add(index);
        animationOrder.push({ index, delay });

        for (let adj of getAdjacentNodes(index)) {
            if (!visited.has(adj)) {
                queue.push({ index: adj, delay: delay + delayFactor });
            }
        }
    }

    const tl = gsap.timeline();

    animationOrder.forEach(({ index, delay }) => {
        const circle = circles[index];
        if (!circle) return;

        tl.to(circle, {
            scale: 5,
            opacity: 1,
            duration: 0.8,
            repeat: -1,
            yoyo: true,
            ease: "power2.out",
            delay,
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
                        <h1 class="text-7xl font-bold text-[#393B45]">Mobile</h1>
                    </div>
                    <div class="w-full h-1/5 flex items-center">
                        <h2 class="text-xl font-normal text-[#393B45]">lorem ipsum dummy text filler</h2>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
