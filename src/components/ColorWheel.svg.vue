<template>
    <div class="svg-container">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" preserveAspectRatio="xMidYMid meet">
            <circle cx="76" cy="60" r="10" fill="#FFD036" class="blend" />
            <circle cx="24" cy="60" r="10" fill="#F20085" class="blend" />
            <circle cx="50" cy="35" r="10" fill="#01AFF6" class="blend" />
        </svg>
    </div>
</template>

<style scoped>
.svg-container {
    position: relative;
    width: 100%;
    height: 100%;
    overflow: visible;
}

svg {
    position: absolute;
    width: 150%;
    height: 150%;
    top: -25%;
    left: -25%;
    overflow: visible;
}

.blend {
    mix-blend-mode: multiply;
    fill-opacity: 0.7;
}
</style>

