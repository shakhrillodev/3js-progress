<template>
  <title>Shakhrillo | ThreeJs Journey</title>
  <div
    :class="[
      'min-h-screen transition-colors duration-300',
      isDark ? 'bg-gray-950 text-gray-100' : 'bg-gray-50 text-gray-900',
    ]"
  >
    <!-- Header -->
    <header
      class="container mx-auto px-6 py-14 flex flex-col items-center text-center relative"
    >
      <!-- Social Links -->
      <div class="flex justify-center gap-4 absolute top-5 left-6">
        <!-- GitHub -->
        <a
          href="https://github.com/shakhrillodev"
          target="_blank"
          class="flex items-center gap-2 px-3 py-1.5 rounded-lg text-sm font-medium border transition-colors duration-300"
          :class="
            isDark
              ? 'bg-gray-800 border-gray-700 text-gray-200 hover:bg-gray-700'
              : 'bg-white border-gray-300 text-gray-800 hover:bg-gray-100'
          "
        >
          <img
            src="/icons/github.svg"
            alt="GitHub"
            class="w-4 h-4"
            :class="isDark ? 'invert' : ''"
          />
          <span>GitHub</span>
        </a>

        <!-- LinkedIn -->
        <a
          href="https://www.linkedin.com/in/shaxrillo-nusratov-9a03a4276/"
          target="_blank"
          class="flex items-center gap-2 px-3 py-1.5 rounded-lg text-sm font-medium border transition-colors duration-300"
          :class="
            isDark
              ? 'bg-gray-800 border-gray-700 text-gray-200 hover:bg-gray-700'
              : 'bg-white border-gray-300 text-gray-800 hover:bg-gray-100'
          "
        >
          <img
            src="/icons/linkedin.svg"
            alt="LinkedIn"
            class="w-4 h-4"
            :class="isDark ? 'invert' : ''"
          />
          <span>LinkedIn</span>
        </a>
      </div>

      <!-- Theme Toggle -->
      <button
        @click="isDark = !isDark"
        class="absolute top-5 right-6 px-3 py-1.5 rounded-lg text-sm font-medium border transition-colors duration-300"
        :class="
          isDark
            ? 'bg-gray-800 border-gray-700 text-gray-200 hover:bg-gray-700'
            : 'bg-white border-gray-300 text-gray-800 hover:bg-gray-100'
        "
      >
        {{ isDark ? "☀️ Light" : "🌙 Dark" }}
      </button>

      <!-- Title -->
      <h1 class="text-4xl md:text-5xl font-bold mb-4">
        My Three.js Journey Projects
      </h1>

      <!-- Subtitle -->
      <p class="max-w-2xl text-gray-500 dark:text-gray-400 mb-8">
        A showcase of creative WebGL experiences I built while following
        <a
          href="https://threejs-journey.com/"
          target="_blank"
          class="text-blue-600 dark:text-blue-400 hover:underline"
        >
          Bruno Simon’s Three.js Journey </a
        >.
      </p>

      <!-- Interaction Notice -->
      <p
        class="text-sm font-medium px-4 py-2 rounded-md border transition-colors duration-300"
        :class="
          isDark
            ? 'border-gray-700 bg-gray-900 text-gray-300'
            : 'border-gray-200 bg-white text-gray-700'
        "
      >
        💡 Feel free to interact with the 3D previews — most are fully
        interactive!
      </p>

      <!-- Full List Button -->
      <div class="mt-6">
        <a
          href="https://3js-build.vercel.app/"
          target="_blank"
          class="inline-flex items-center gap-2 px-4 py-2 rounded-lg text-sm font-medium border transition-all duration-300"
          :class="
            isDark
              ? 'bg-gray-800 border-gray-700 text-gray-200 hover:bg-gray-700 hover:translate-x-1'
              : 'bg-white border-gray-300 text-gray-800 hover:bg-gray-100 hover:translate-x-1'
          "
        >
          🌐 List of My Journey So Far →
        </a>
      </div>
    </header>

    <!-- Project Grid -->
    <main class="container mx-auto px-6 pb-20">
      <div class="grid sm:grid-cols-2 md:grid-cols-3 xl:grid-cols-4 gap-8">
        <Card
          v-for="(project, i) in projects"
          :key="i"
          class="grid grid-rows-[auto_1fr_auto] gap-0 group overflow-hidden rounded-2xl border transition-all duration-300 hover:-translate-y-1 hover:shadow-xl p-0"
          :class="
            isDark
              ? 'bg-gray-900 border-gray-800 hover:border-gray-700'
              : 'bg-white border-gray-200 hover:border-gray-300'
          "
        >
          <!-- Image Hover -->
          <div class="relative w-full h-52 overflow-hidden">
            <img
              :src="`/${project.image}`"
              :alt="project.title + ' image'"
              class="absolute inset-0 w-full h-full object-cover transition-opacity duration-700 rounded-t-2xl opacity-100 group-hover:opacity-0"
            />
            <img
              :src="`/${project.gif}`"
              :alt="project.title + ' animation'"
              class="absolute inset-0 w-full h-full object-cover transition-opacity duration-700 rounded-t-2xl opacity-0 group-hover:opacity-100"
            />
          </div>

          <!-- Text -->
          <div class="p-3">
            <h2
              class="text-lg font-semibold mb-2"
              :class="isDark ? 'text-amber-50' : ''"
            >
              {{ project.title }}
            </h2>
            <p class="text-sm text-gray-600 dark:text-gray-400">
              {{ project.description }}
            </p>
          </div>
          <div class="p-3">
            <a
              :href="project.preview"
              target="_blank"
              class="block w-full text-center py-2 rounded-lg font-medium transition"
              :class="
                isDark
                  ? 'bg-blue-600 hover:bg-blue-500 text-white'
                  : 'bg-blue-600 hover:bg-blue-500 text-white'
              "
            >
              Preview
            </a>
          </div>
        </Card>
      </div>
    </main>
  </div>
</template>

<script setup lang="ts">
import { Card } from "@/components/ui/card";

const isDark = ref(true);

const projects = [
  {
    image: "portal/portal.png",
    gif: "portal/portal.gif",
    description:
      "A magical animated portal scene demonstrating shader-based materials, custom geometries, and particle glow effects in Three.js. It uses noise functions and time-based uniforms to create a dynamic swirling energy effect around the portal opening.",
    preview: "https://3js-build.vercel.app/portal",
    title: "Portal Scene",
  },
  {
    image: "3d_text/3d_text.png",
    gif: "3d_text/3d_text.gif",
    preview:
      "https://3js-build.vercel.app/builds/0009-8030a1a-12---3D-Text.html",
    title: "3D Text",
    description:
      "Creates large floating 3D typography using Three.js’s TextGeometry. Explores font loading, extrusion depth, and basic material styling.",
  },
  {
    image: "coffee_smoke/coffee_smoke.png",
    gif: "coffee_smoke/coffee_smoke.gif",
    preview:
      "https://3js-build.vercel.app/builds/0036-2a6a6c5-32---Coffee-Smoke.html",
    title: "Coffee Smoke",
    description:
      "Simulates delicate smoke particles rising around a coffee cup by using custom shaders and particle systems for a realistic volumetric feel.",
  },
  {
    image: "earth/earth.png",
    gif: "earth/earth.gif",
    preview: "https://3js-build.vercel.app/builds/0047-fc254f1-382-Earth.html",
    title: "Earth",
    description:
      "Renders a realistic Earth sphere with texture maps, lighting, and rotation, demonstrating environment mapping and shader-based lighting.",
  },
  {
    image: "env_map_mirror/env_map_mirror.png",
    gif: "env_map_mirror/env_map_mirror.gif",
    preview:
      "https://3js-build.vercel.app/builds/0022-fcf4405-242---Environment-map.html",
    title: "Environment Map Mirror",
    description:
      "Uses a cube texture loader to simulate reflective surfaces — turns objects into mirrors of the surrounding scene using environment mapping.",
  },
  {
    image: "fireworks/fireworks.png",
    gif: "fireworks/fireworks.gif",
    preview:
      "https://3js-build.vercel.app/builds/0041-254382f-342---Fireworks.html",
    title: "Fireworks",
    description:
      "Creates burst particle animations with physics and shaders to simulate fireworks exploding and scattering in a 3D space.",
  },
  {
    image: "fox_animation/fox_animation.png",
    gif: "fox_animation/fox_animation.gif",
    preview:
      "https://3js-build.vercel.app/builds/0024-f06c1e3-26---Code-structuring-for-pigger-projects.html",
    title: "Fox Animation",
    description:
      "Animates a fox model with skeletal animation and Three.js mixers, exploring model loading, animation blending and playback control.",
  },
  {
    image: "gpgpu_boat/gpgpu_boat.png",
    gif: "gpgpu_boat/gpgpu_boat.gif",
    preview:
      "https://3js-build.vercel.app/builds/0057-9870022-41-GPGPU-flow-field-particles-shader.html",
    title: "GPGPU Boat",
    description:
      "Implements GPU-accelerated physics for many objects (boats) using GPGPU techniques for high-performance simulation in WebGL.",
  },
  {
    image: "hologram/hologram.png",
    gif: "hologram/hologram.gif",
    preview:
      "https://3js-build.vercel.app/builds/0039-ebd0db9-33---Hologram-shader.html",
    title: "Hologram",
    description:
      "Creates a sci-fi holographic material via Fresnel effect and glitch-vertex animations to simulate hologram flicker.",
  },
  {
    image: "hounted_house/hounted_house.png",
    gif: "hounted_house/hounted_house.gif",
    preview:
      "https://3js-build.vercel.app/builds/0012-9be625b-17---Haunted-house.html",
    title: "Haunted House",
    description:
      "Builds a spooky scene with primitives, textured walls and floating lights to evoke a haunted house atmosphere—first real-time environment.",
  },
  {
    image: "morphing_particles/morphing_particles.png",
    gif: "morphing_particles/morphing_particles.gif",
    preview:
      "https://3js-build.vercel.app/builds/0053-cd6a93a-401-Particles-morphing-shader.html",
    title: "Morphing Particles",
    description:
      "Transitions between multiple particle shapes and states using buffer attributes and shader morphing, exploring GPU data transforms.",
  },
  {
    image: "parallax_animation/parallax_animation.png",
    gif: "parallax_animation/parallax_animation.gif",
    preview:
      "https://3js-build.vercel.app/builds/0015-7509f49-19---Scroll-animation-and-Parallax.html",
    title: "Parallax Animation",
    description:
      "Uses multiple layers and camera motion to create a parallax effect with Three.js, blending 2D and 3D movements for immersive depth.",
  },
  {
    image: "particle_cursor_animation/particle_cursor_animation.png",
    gif: "particle_cursor_animation/particle_cursor_animation.gif",
    preview:
      "https://3js-build.vercel.app/builds/0051-87536e6-393-Particles-cursor-animation-update.html",
    title: "Particle Cursor Animation",
    description:
      "Follows the mouse or pointer and emits particles accordingly, combining ray-casting and particle systems for interactive effect.",
  },
  {
    image: "particle_galaxy/particle_galaxy.png",
    gif: "particle_galaxy/particle_galaxy.gif",
    preview:
      "https://3js-build.vercel.app/builds/0034-4380de6-30---Animated-galaxy-redo.html",
    title: "Particle Galaxy",
    description:
      "Creates a massive galaxy of points with shader-based procedural textures, putting you in the center of a deep 3D star field.",
  },
  {
    image: "raging_sea_shader/raging_sea_shader.png",
    gif: "raging_sea_shader/raging_sea_shader.gif",
    preview:
      "https://3js-build.vercel.app/builds/0044-a9762f2-36-Raging-Sea-Shading.html",
    title: "Raging Sea Shader",
    description:
      "Simulates ocean waves in real time by manipulating vertex positions and normals using sine functions and shader logic.",
  },
  {
    image: "slice_model/slice_model.png",
    gif: "slice_model/slice_model.gif",
    preview:
      "https://3js-build.vercel.app/builds/0060-8207503-43-Slice-Model-Shader.html",
    title: "Slice Model",
    description:
      "Demonstrates advanced clipping in 3D: slices through a 3D model using shader-based discarding.",
  },
  {
    image: "wooble_sphere/wooble_sphere.png",
    gif: "wooble_sphere/wooble_sphere.gif",
    preview:
      "https://3js-build.vercel.app/builds/0059-b36a2cb-42-Wobbly-sphere-shader.html",
    title: "Wobble Sphere",
    description:
      "Shows a wobbling sphere influenced by noise and time-based deformation, exploring vertex displacement and cyclic animations.",
  },
];
</script>
