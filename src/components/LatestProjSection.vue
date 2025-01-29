<template>
  <section class="text-white mt-20" id="projects">
    <div class="px-4 xl:pl-16">
      <div class="mb-4 md:flex md:justify-between xl:pr-16">
        <h2 class="text-4xl font-bold text-white">My Latest Projects</h2>
        <div class="flex space-x-4 mb-4 mt-5 md:mt-0">
          <button
            class="hover:text-primary"
            v-for="category in ['all', 'web development', 'Mobile App']"
            :key="category"
            @click="() => (selectedCategory = category)"
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
          <div
            class="h-52 md:h-[24rem] rounded-t-xl relative group"
            :style="{
              backgroundImage: 'url(' + project.image + ')',
              backgroundSize: 'cover',
            }"
          >
            <div
              class="overlay items-center justify-center absolute top-0 left-0 w-full h-full bg-[#181818] bg-opacity-0 hidden group-hover:flex group-hover:bg-opacity-80 transition-all duration-500"
            >
              <!-- Left Button: GitHub Source Code -->
              <a
                class="h-14 w-14 mr-2 border-2 relative rounded-full border-[#ADB7BE] hover:border-white group/link"
                :href="project.gitURL"
                target="_blank"
                rel="noopener noreferrer"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  aria-hidden="true"
                  data-slot="icon"
                  class="h-10 w-10 text-[#ADB7BE] absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 cursor-pointer group-hover/link:text-white"
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
                  ></path></svg
              ></a>
            </div>
          </div>
          <div
            class="text-white rounded-b-xl mt-3 bg-[#111a3e] shadow-lg border border-[#1f1641] py-6 px-4"
          >
            <!-- Centered, Clickable Subheading -->
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

  const Projects = ref([
    {
      id: 1,
      category: 'DevOps & Automation',
      image: 'src/assets/projects/id1.png',
      title: 'CI Engine',
      description:
        'A lightweight CI/CD pipeline service for seamless developer workflow integration. Automate builds, tests, and deployments with CLI tools and Docker support.',
      technologies: ['Python', 'CLI Tools', 'Docker', 'Git', 'MongoDB'],
      gitURL: 'https://github.com/akshayrao96/ci-engine',
    },
    {
      id: 2,
      category: 'Full Stack Development',
      image: 'src/assets/projects/id2.jpg',
      title: 'Password Manager Vault',
      description:
        'A secure, full-stack password manager with encrypted storage. Built with React and Node.js, it supports user authentication and role-based access. Currently in progress.',
      technologies: ['JavaScript', 'NodeJS', 'React', 'HTML', 'CSS', 'MongoDB'],
      gitURL: 'https://github.com/akshayrao96/password-manager-vault',
    },
    {
      id: 3,
      category: 'Distributed Systems',
      image: 'src/assets/projects/id3.jpg',
      title: 'Distributed Album Store',
      description:
        'A scalable album store built on AWS, integrating dynamic server frameworks, load balancing, and RabbitMQ for high throughput and reliability.',
      technologies: ['Java', 'Servlets', 'DynamoDB', 'MySQL', 'AWS'],
      gitURL: 'https://github.com/akshayrao96/distributed-album-store',
    },
    {
      id: 4,
      category: 'Microservices',
      image: 'src/assets/projects/id4.jpg',
      title: 'Katallage',
      description:
        'A dynamic e-commerce platform enabling users to buy and offer freelance services. Built with microservices architecture and Kubernetes deployment. Currently in progress.',
      technologies: [
        'TypeScript',
        'RabbitMQ',
        'Kubernetes',
        'Grafana',
        'Prometheus',
      ],
      gitURL: 'https://github.com/akshayrao96/katallage',
    },
    {
      id: 5,
      category: 'System Programming',
      image: 'src/assets/projects/id5.png',
      title: 'Task Scheduler',
      description:
        'A Linux kernel-inspired task scheduler simulator, implementing priority-based scheduling and resource allocation for process management. Analyzes metrics and tradeoffs for different scheduling algorithms.',
      technologies: ['C++'],
      gitURL: 'https://github.com/yourrepo/task-scheduler',
    },
    {
      id: 6,
      category: 'Networking & Communication',
      image: 'src/assets/projects/id6.jpg',
      title: 'Chat Program',
      description:
        'A Python-based chat application to reinforce networking concepts like TCP/IP, multithreading, and web sockets. Includes a GUI for enhanced usability.',
      technologies: ['Python', 'TCP/IP', 'Multithreading'],
      gitURL: 'https://github.com/akshayrao96/chat-program',
    },
  ]);

  const selectedCategory = ref('all');
  const filteredProjects = computed(() => {
    if (selectedCategory.value === 'all') {
      return Projects.value;
    }
    return Projects.value.filter(
      project =>
        project.category.toLowerCase() === selectedCategory.value.toLowerCase()
    );
  });
</script>
