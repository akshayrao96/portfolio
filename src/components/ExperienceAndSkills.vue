<template>
  <section class="text-white mt-18" id="skills">
    <div class="absolute right-0 top-[110rem] h-full w-full justify-end">
      <span class="flex opacity-20">
        <span class="w-16 h-32 rounded-l-full flex bg-primary blur-2xl"></span>
        <span
          class="w-16 h-32 rounded-r-full flex bg-[#f88fc2] blur-2xl mt-14"
        ></span>
      </span>
    </div>
    <div
      class="md:grid md:grid-cols-2 gap-8 items-center py-8 px-4 xl:gap-16 xl:px-16"
    >
      <div class="mt-4 md:mt-0 text-left flex flex-col z-10 h-full w-[80%]">
        <h2 class="text-4xl font-bold text-white text-left mb-4">
          My
          <span
            class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary"
          >
            Skills
          </span>
        </h2>

        <div class="mt-8" v-for="domain in SkillDomains" :key="domain.id">
          <!-- Domain Name -->
          <h4
            class="font-semibold uppercase text-white text-lg"
            data-aos="fade-right"
          >
            {{ domain.name }}
          </h4>

          <!-- Tech Stack List with Animation & Balanced Size -->
          <div class="flex flex-wrap mt-3 gap-3">
            <span
              v-for="tech in domain.tech"
              :key="tech"
              class="px-5 py-2.5 border-2 border-[#FFD700] rounded-xl text-white text-base font-medium shadow-lg scale-95 animate-fadeIn transition-all duration-300 ease-in-out hover:scale-105"
            >
              {{ tech }}
            </span>
          </div>
        </div>
      </div>
      <div data-aos="flip-left">
        <h2
          class="text-4xl font-bold text-white text-left mb-8 md:text-center md:mt-0 mt-8"
        >
          Recent Career Experiences
        </h2>
        <div class="space-y-8 py-8" data-aos="fade-left">
          <div
            v-for="element in Experinces"
            :key="element.id"
            class="flex items-center rounded-xl p-4 bg-[#111a3e] shadow-lg border border-[#1f1641]"
          >
            <div class="w-1/4">
              <img
                :src="getImagePath(element.image)"
                :alt="element.company"
                class="w-28 h-28 max-w-full object-contain border-1"
              />
            </div>
            <div class="w-3/4 pl-4">
              <h3
                class="text-2xl font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary"
              >
                {{ element.role }}
              </h3>
              <p class="text-white text-lg">{{ element.company }}</p>
              <p class="text-white text-lg">{{ element.date }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<script setup>
  import { ref } from 'vue';

  const getImagePath = imageName => {
    return new URL(`../assets/${imageName}`, import.meta.url).href;
  };

  const SkillDomains = ref([
    {
      id: 1,
      name: 'Frontend Development',
      tech: ['React', 'React Native', 'Vue.js'],
    },
    {
      id: 2,
      name: 'Backend Development',
      tech: ['Python', 'Java', 'JavaScript', 'TypeScript', 'Golang'],
    },
    {
      id: 3,
      name: 'Server-Side Frameworks',
      tech: ['Flask', 'FastAPI', 'Spring', 'Servlets', 'Node.js', 'Gin'],
    },
    {
      id: 4,
      name: 'Databases & Data Management',
      tech: ['PostgreSQL', 'MySQL', 'MongoDB', 'DynamoDB', 'Redis'],
    },
    {
      id: 5,
      name: 'DevOps, Cloud & Infrastructure',
      tech: ['Docker', 'Kubernetes', 'CircleCI', 'YAML'],
    },
  ]);

  const Experinces = ref([
    {
      id: 1,
      role: 'Software Dev Engineer',
      company: 'Amazon',
      date: 'July 2025 - Current',
      image: 'aws_logo.png',
    },
    {
      id: 2,
      role: 'Devops Engineer',
      company: 'Crely Inc.',
      date: 'February 2025 - June 2025',
      image: 'crely_inc_logo.jpg',
    },
    {
      id: 3,
      role: 'Software Engineer Intern',
      company: 'Insightsoftware - JustPerform',
      date: 'May 2024 - September 2024',
      image: 'insightsoftware_logo.jpg',
    },
    {
      id: 4,
      role: 'Software Developer',
      company: 'Yara International',
      date: 'February 2022 - August 2022',
      image: 'yara_logo.png',
    },

    {
      id: 5,
      role: 'Teaching Assistant',
      company: 'Northeastern University',
      date: 'January 2023 - December 2024',
      image: 'neu_husky.png',
    },
  ]);
</script>
