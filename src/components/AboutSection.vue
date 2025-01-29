<template>
  <section class="text-white mt-16" id="about">
    <div class="absolute z-0 top-[92rem] inset-x-0 h-64 flex items-start">
      <div
        class="h-24 w-64 bg-gradient-to-br from-primary via-secondary blur-2xl to-[#570cac] opacity-20"
      ></div>
    </div>
    <div
      class="md:grid md:grid-cols-2 gap-8 items-center py-6 px-4 xl:gap-16 sm:py-12 xl:px-16 z-1"
    >
      <div data-aos="flip-right">
        <h2 class="text-5xl font-bold text-white text-center mb-6">
          My Education
        </h2>
        <div class="space-y-8 py-6">
          <div
            v-for="element in education"
            :key="element.id"
            class="flex items-center md:w-[85%] w-full rounded-xl bg-[#111a3e] shadow-lg border border-[#1f1641] p-4"
          >
            <div class="w-1/4 flex justify-center">
              <img
                :src="getImagePath(element.image)"
                :alt="element.school"
                class="w-28 h-28 max-w-full object-contain border-1"
                style="border-color: #654321"
              />
            </div>
            <div class="w-3/4 pl-4">
              <h3
                class="text-2xl font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary lg:text-2xl"
              >
                {{ element.school }}
              </h3>
              <p class="text-white text-lg">{{ element.program }}</p>
              <p class="text-white text-lg">{{ element.year }}</p>
            </div>
          </div>
        </div>
      </div>
      <div
        class="mt-4 md:mt-0 text-left flex flex-col z-10 h-full"
        data-aos="flip-right"
      >
        <h2 class="text-5xl font-bold text-white md:text-center text-left mb-6">
          More
          <span
            class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary"
            >About</span
          >
          Me
        </h2>
        <p class="text-xl lg:text-2xl mt-4 mb-6 leading-relaxed">
          Originally from Singapore and now based in Seattle, I'm passionate
          about learning and embracing new experiences. My hobbies include
          listening to podcasts, reading biographies, watching sports, staying
          active, and exploring unique cafes.
        </p>
        <p class="text-xl lg:text-2xl leading-relaxed">
          I find joy in meeting people and hearing their unique stories.
          Additionally, I love traveling, especially immersing myself in
          different cultures. These experiences have shaped my perspective and
          fueled my passion for continuous growth.
        </p>
      </div>
    </div>
  </section>
</template>

<script setup>
  import { ref } from 'vue';

  const getImagePath = imageName => {
    return new URL(`../assets/${imageName}`, import.meta.url).href;
  };

  const education = ref([
    {
      id: 1,
      school: 'Northeastern University, Seattle',
      program: 'MS Computer Science',
      year: '2022 - 2024',
      image: 'neu_logo.png',
    },
    {
      id: 2,
      school: 'University of Washington, Seattle',
      program: 'BS Biochemistry',
      year: '2017 - 2021',
      image: 'uw_logo.jpg',
    },
  ]);
</script>
