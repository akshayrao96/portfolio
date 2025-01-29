<template>
  <section class="text-white mt-20" id="projects">
    <div class="px-4 xl:pl-16">
      <div class="mb-4 md:flex md:justify-between xl:pr-16">
        <h2 class="text-4xl font-bold text-white">My Latest Projects</h2>

        <!-- Simple Clickable Category Filters (No Borders, Clean Look) -->
        <div class="flex flex-wrap gap-4 mb-4 mt-5 md:mt-0">
          <button
            v-for="category in categories"
            :key="category"
            @click="selectedCategory = category"
            class="text-white text-lg transition-all duration-300"
            :class="{
              'text-primary font-semibold': selectedCategory === category,
              'hover:text-primary': selectedCategory !== category,
            }"
          >
            {{ category }}
          </button>
        </div>
      </div>

      <ul
        class="px-4 sm:py-16 xl:pr-16 grid grid-cols-1 gap-6 pt-10 sm:grid-cols-2 md:gap-10 md:pt-12 lg:grid-cols-3"
        data-aos="fade-right"
      >
        <div v-for="project in filteredProjects" :key="project.id">
          <a
            :href="project.gitURL"
            target="_blank"
            rel="noopener noreferrer"
            class="block h-52 md:h-[24rem] rounded-t-xl relative group transition-all duration-300 hover:scale-105"
            :style="{
              backgroundImage: 'url(' + project.image + ')',
              backgroundSize: 'cover',
            }"
          >
            <div
              class="overlay items-center justify-center absolute top-0 left-0 w-full h-full bg-[#181818] bg-opacity-0 hidden group-hover:flex group-hover:bg-opacity-80 transition-all duration-500"
            >
              <div class="h-14 w-14 relative flex items-center justify-center">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  class="h-10 w-10 text-[#ADB7BE] group-hover:text-white transition-all duration-300"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M2.036 12.322a1.012 1.012 0 0 1 0-.639C3.423 7.51 7.36 4.5 12 4.5c4.638 0 8.573 3.007 9.963 7.178.07.207.07.431 0 .639C20.577 16.49 16.64 19.5 12 19.5c-4.638 0-8.573-3.007-9.963-7.178Z"
                  ></path>
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M15 12a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z"
                  ></path>
                </svg>
              </div>
            </div>
          </a>
          <div
            class="text-white rounded-b-xl mt-3 bg-[#111a3e] shadow-lg border border-[#1f1641] py-6 px-4"
          >
            <h3 class="text-lg font-semibold uppercase lg:text-xl text-center">
              <a
                :href="project.gitURL"
                target="_blank"
                rel="noopener noreferrer"
                class="hover:text-primary transition-all duration-300"
              >
                {{ project.title }}
              </a>
            </h3>
            <p class="text-[#ADB7BE] text-center">{{ project.description }}</p>
            <div class="flex flex-wrap justify-center p-2.5">
              <div
                v-for="technology in project.technologies"
                :key="technology"
                class="text-center ml-1 mt-1 rounded-3xl bg-[#111827]"
                style="
                  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
                  border: 1px solid #111827;
                  backdrop-filter: blur(9px);
                  -webkit-backdrop-filter: blur(9px);
                "
              >
                <p class="px-3 py-2">{{ technology }}</p>
              </div>
            </div>
          </div>
        </div>
      </ul>
    </div>
  </section>
</template>
<script setup>
  import { ref, computed } from 'vue';

  const categories = ref([
    'Distributed Systems',
    'DevOps & Automation',
    'Full-Stack Development',
    'Systems Programming',
    'Computer Networking',
  ]);

  const selectedCategory = ref('All');

  const Projects = ref([
    {
      id: 1,
      categories: ['Systems Programming'],
      image: 'src/assets/projects/id1.png',
      title: 'CI Engine',
      description:
        'A robust CI/CD service designed to streamline developer workflow integration. This system automates build, test, and deployment pipelines, ensuring seamless code delivery.',
      technologies: ['Python', 'CLI Tools', 'Docker', 'Git', 'MongoDB'],
      gitURL: 'https://github.com/akshayrao96/ci-engine',
    },
    {
      id: 2,
      categories: ['Full-Stack Development'],
      image: 'src/assets/projects/id2.jpg',
      title: 'Password Manager Vault',
      description:
        'A password manager for storing passwords securely. Includes a full-stack application that manages users, ownership rights, and password encryption.',
      technologies: ['JavaScript', 'NodeJS', 'React', 'HTML', 'CSS', 'MongoDB'],
      gitURL: 'https://github.com/akshayrao96/password-manager-vault',
    },
    {
      id: 3,
      categories: ['Distributed Systems'],
      image: 'src/assets/projects/id3.jpg',
      title: 'Distributed Album Store',
      description:
        'Client and server system for an optimized distributed architecture. Hosted on AWS, scales via dynamic frameworks, load balancing, and RabbitMQ integration for high throughput.',
      technologies: ['Java', 'RabbitMQ', 'DynamoDB', 'MySQL', 'AWS'],
      gitURL: 'https://github.com/akshayrao96/distributed-album-store',
    },
    {
      id: 4,
      categories: [
        'Microservices',
        'Distributed Systems',
        'Full-Stack Development',
      ],
      image: 'src/assets/projects/id4.jpg',
      title: 'Katallage',
      description:
        'An e-commerce platform where users can buy or sell services. Uses event-based microservices architecture using Kubernetes as orchestration management, RabbitMQ, and observability tools.',
      technologies: [
        'TypeScript',
        'Redis',
        'Kubernetes',
        'Grafana',
        'Prometheus',
      ],
      gitURL: 'https://github.com/akshayrao96/katallage',
    },
    {
      id: 5,
      categories: ['Systems Programming'],
      image: 'src/assets/projects/id5.png',
      title: 'Task Scheduler',
      description:
        'A simulation of a Linux-based task scheduler, implementing multiple scheduling algorithms and resource allocation methods. Analyzes metrics and tradeoffs between algorithms.',
      technologies: ['C++'],
      gitURL: 'https://github.com/yourrepo/task-scheduler',
    },
    {
      id: 6,
      categories: ['Computer Networking'],
      image: 'src/assets/projects/id6.jpg',
      title: 'Chat Program',
      description:
        'A Python-based chat application for learning networking fundamentals (TCP/IP, multithreading, web sockets). Includes a GUI for an enhanced user experience.',
      technologies: ['Python', 'TCP/IP', 'Multithreading'],
      gitURL: 'https://github.com/akshayrao96/chat-program',
    },
  ]);

  const filteredProjects = computed(() => {
    if (selectedCategory.value === 'All') return Projects.value;
    return Projects.value.filter(project =>
      project.categories.includes(selectedCategory.value)
    );
  });
</script>
