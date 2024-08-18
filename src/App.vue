<template>
  <div
    class="not-selectable relative flex h-screen w-full flex-col items-center justify-center gap-4 bg-[#222222]"
  >
    <div
      class="absolute left-1 top-1 bg-[#222222] text-[16px] font-medium text-[#f0f0f0]"
    >
      <h1>mouseDownY: {{ mouseDownY }}px</h1>
      <h1>mouseDownX: {{ mouseDownX }}px</h1>
      <h1>prevDeltaX: {{ prevDeltaX }}px</h1>
      <h1>prevDeltaY: {{ prevDeltaY }}px</h1>
      <h1>deltaX: {{ deltaX }}deg</h1>
      <h1>deltaY: {{ deltaY }}deg</h1>
    </div>

    <div class="h-96 w-96 contrast-75">
      <div
        id="outer"
        class="relative h-96 w-96"
        :style="{
          'transform-style': 'preserve-3d',

          transform: `rotateX(${-deltaY}deg) rotateY(${deltaX}deg`,
        }"
        @dblclick="openCube = !openCube"
      >
        <div
          id="inner"
          class="absolute left-1/2 top-1/2 h-64 w-64 -translate-x-1/2 -translate-y-1/2"
          :style="{
            'transform-style': 'preserve-3d',
          }"
        >
          <div
            class="absolute h-64 w-64 rounded-[0px] bg-red-400 opacity-80 transition-all duration-1000"
            :class="`${openCube ? 'border-0 border-[transparent]' : 'border-4 border-violet-300'}`"
            :style="{
              transform: `${openCube ? 'translateZ(256px)' : 'translateZ(128px)'}`,
            }"
          ></div>
          <div
            class="absolute h-64 w-64 rounded-[0px] bg-orange-400 opacity-80 transition-all duration-1000"
            :class="`${openCube ? 'border-0 border-[transparent]' : 'border-4 border-violet-300'}`"
            :style="{
              transform: `rotateY(180deg) ${openCube ? 'translateZ(256px)' : 'translateZ(128px)'} `,
            }"
          ></div>
          <div
            class="absolute h-64 w-64 rounded-[0px] bg-yellow-400 opacity-80 transition-all duration-1000"
            :class="`${openCube ? 'border-0 border-[transparent]' : 'border-4 border-violet-300'}`"
            :style="{
              transform: `rotateY(90deg) ${openCube ? 'translateZ(256px)' : 'translateZ(128px)'} `,
            }"
          ></div>
          <div
            class="absolute h-64 w-64 rounded-[0px] bg-green-400 opacity-80 transition-all duration-1000"
            :class="`${openCube ? 'border-0 border-[transparent]' : 'border-4 border-violet-300'}`"
            :style="{
              transform: `rotateY(-90deg) ${openCube ? 'translateZ(256px)' : 'translateZ(128px)'} `,
            }"
          ></div>
          <div
            class="absolute h-64 w-64 rounded-[0px] bg-blue-400 opacity-80 transition-all duration-1000"
            :class="`${openCube ? 'border-0 border-[transparent]' : 'border-4 border-violet-300'}`"
            :style="{
              transform: `rotateX(90deg) ${openCube ? 'translateZ(256px)' : 'translateZ(128px)'} `,
            }"
          ></div>
          <div
            class="absolute h-64 w-64 rounded-[0px] bg-indigo-400 opacity-80 transition-all duration-1000"
            :class="`${openCube ? 'border-0 border-[transparent]' : 'border-4 border-violet-300'}`"
            :style="{
              transform: `rotateX(-90deg) ${openCube ? 'translateZ(256px)' : 'translateZ(128px)'} `,
            }"
          ></div>
        </div>
      </div>
    </div>

    <div class="absolute bottom-1 right-1 flex flex-col gap-1">
      <div class="flex flex-col items-center justify-center gap-0.5">
        <h1 class="font-medium text-violet-300">Smooth</h1>
        <div
          class="flex h-8 w-full items-center justify-start rounded-full border-2 border-[#f0f0f0] p-1 transition-all duration-500"
          :class="smooth ? 'border-violet-300' : 'border-[#f0f0f0] opacity-50'"
          @click="switchSmooth"
        >
          <div
            class="aspect-square h-full rounded-full transition-all duration-500"
            :class="
              smooth
                ? 'ml-[72%] bg-violet-300'
                : 'ml-[0%] bg-[#f0f0f0] opacity-50'
            "
          ></div>
        </div>
      </div>
      <button
        class="rounded-[8px] border-2 border-violet-300 px-4 py-0.5 font-medium text-violet-300"
        @click="openCube = !openCube"
      >
        {{ openCube ? "Shrink" : "Spread" }}
      </button>
      <button
        class="rounded-[8px] border-2 border-violet-300 px-4 py-0.5 font-medium text-violet-300"
        @click="reset"
      >
        Reset
      </button>
    </div>

    <div class="absolute bottom-1 left-1 flex flex-col gap-1">
      <div
        class="phone:flex-row flex flex-col items-center justify-center gap-2"
      >
        <h1 class="font-medium text-violet-300 transition-all duration-500">
          Developed by
        </h1>

        <div class="flex gap-2">
          <a
            target="_blank"
            href="https://ammarabdelwadoudv2.netlify.app"
            class="underline underline-offset-2"
          >
            <div
              class="logo -my-1 size-8 bg-violet-300 transition-colors duration-500"
            ></div>
          </a>
          <a
            class="transition-colors duration-500"
            target="_blank"
            href="https://github.com/Dangoxy"
          >
            <svg
              class="transition-colors duration-500"
              :fill="'#c4b5fd'"
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
            >
              <path
                d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
              />
            </svg>
          </a>
          <a
            class="transition-colors duration-500"
            target="_blank"
            href="https://www.linkedin.com/in/ammar-abdelwadoud-20457a272/"
          >
            <svg
              class="transition-colors duration-500"
              :fill="'#c4b5fd'"
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
            >
              <path
                d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"
              />
            </svg>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

let mouseDownY = ref(0);
let mouseDownX = ref(0);

let prevDeltaX = ref(-8);
let prevDeltaY = ref(-8);

let deltaX = ref(-8);
let deltaY = ref(-8);

let openCube = ref(false);
let smooth = ref(true);

function reset() {
  prevDeltaX.value = -8;
  prevDeltaY.value = -8;

  deltaX.value = -8;
  deltaY.value = -8;

  document.getElementById("outer")?.animate(
    {
      transform: `rotateX(${-deltaY.value}deg) rotateY(${deltaX.value}deg)`,
    },
    {
      duration: 2000,
      easing: "ease-in-out",
      fill: "forwards",
    },
  );
}

function switchSmooth() {
  smooth.value = !smooth.value;
}

window.onmousedown = (e) => {
  mouseDownX.value = e.clientX;
  mouseDownY.value = e.clientY;
};

window.onmousemove = (e) => {
  if (mouseDownX.value !== 0 && mouseDownY.value !== 0) {
    deltaX.value = prevDeltaX.value + (e.clientX - mouseDownX.value);
    deltaY.value = prevDeltaY.value + (e.clientY - mouseDownY.value);

    document.getElementById("outer")?.animate(
      {
        transform: `rotateX(${-deltaY.value}deg) rotateY(${deltaX.value}deg)`,
      },
      {
        duration: smooth.value ? 5000 : 0,
        easing: "ease",
        fill: "forwards",
      },
    );
  }
};

window.onmouseup = () => {
  mouseDownX.value = 0;
  mouseDownY.value = 0;

  prevDeltaX.value = deltaX.value;
  prevDeltaY.value = deltaY.value;
};

window.ontouchstart = (e) => {
  mouseDownX.value = e.touches[0].clientX;
  mouseDownY.value = e.touches[0].clientY;
};

window.ontouchmove = (e) => {
  if (mouseDownX.value !== 0 && mouseDownY.value !== 0) {
    deltaX.value = prevDeltaX.value + (e.touches[0].clientX - mouseDownX.value);
    deltaY.value = prevDeltaY.value + (e.touches[0].clientY - mouseDownY.value);

    document.getElementById("outer")?.animate(
      {
        transform: `rotateX(${-deltaY.value}deg) rotateY(${deltaX.value}deg)`,
      },
      { duration: 5000, easing: "ease", fill: "forwards" },
    );
  }
};

window.ontouchend = () => {
  mouseDownX.value = 0;
  mouseDownY.value = 0;

  prevDeltaX.value = deltaX.value;
  prevDeltaY.value = deltaY.value;
};
</script>

<style scoped>
.logo {
  -webkit-mask: url(../public/devIcon3.svg) no-repeat center;
  mask: url(../public/devIcon3.svg) no-repeat center;

  -webkit-mask-size: contain;
  mask-size: contain;
}

.not-selectable {
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
</style>
