<template>
  <section class="text-white mt-20" id="contact">
    <h2 class="text-4xl font-bold text-white text-left mb-4 px-4 xl:pl-16">
      Let's Connect
    </h2>
    <div
      class="grid md:grid-cols-2 gap-4 relative px-4 xl:px-16 mt-8"
      data-aos="zoom-in-up"
    >
      <!-- Left Side: Contact Information -->
      <div>
        <p class="text-[#adb7be]">
          I'm always excited to connect with fellow developers, engineers, and
          tech enthusiasts! Whether it's discussing software, open-source
          contributions, or new opportunities, feel free to reach out via email
          or connect on LinkedIn and GitHub.
        </p>
        <div class="col-lg-4 col-md-4 mb-lg-0 mt-5">
          <!-- Email -->
          <div class="flex mb-10 items-center">
            <div
              class="p-2 bg-[#111a3e] w-[50px] h-[46px] flex justify-center rounded-full overflow-hidden border border-[#111a3e] backdrop-blur"
            >
              <img
                src="https://img.icons8.com/metro/50/ffffff/new-post.png"
                alt="email"
                class="w-6"
              />
            </div>
            <div class="ml-5 text-white">
              <h4>Email</h4>
              <p>akshayrao196@gmail.com</p>
            </div>
          </div>
          <!-- GitHub -->
          <div class="flex mb-10 items-center">
            <div
              class="p-2 bg-[#111a3e] w-[50px] h-[46px] flex justify-center rounded-full overflow-hidden border border-[#111a3e] backdrop-blur"
            >
              <img
                src="https://img.icons8.com/ios-filled/50/ffffff/github.png"
                alt="github"
                class="w-6"
              />
            </div>
            <div class="ml-5 text-white">
              <h4>GitHub</h4>
              <p>
                <a
                  href="https://github.com/akshayrao96"
                  target="_blank"
                  class="text-primary hover:underline"
                  >github.com/akshayrao96</a
                >
              </p>
            </div>
          </div>
          <!-- LinkedIn -->
          <div class="flex mb-10 items-center">
            <div
              class="p-2 bg-[#111a3e] w-[50px] h-[46px] flex justify-center rounded-full overflow-hidden border border-[#111a3e] backdrop-blur"
            >
              <img
                src="https://img.icons8.com/ios-filled/50/ffffff/linkedin.png"
                alt="linkedin"
                class="w-6"
              />
            </div>
            <div class="ml-5 text-white">
              <h4>LinkedIn</h4>
              <p>
                <a
                  href="https://www.linkedin.com/in/akshay-rao-bhamidipati/"
                  target="_blank"
                  class="text-primary hover:underline"
                  >linkedin.com/in/akshay-rao-bhamidipati</a
                >
              </p>
            </div>
          </div>
        </div>
      </div>

      <!-- Right Side: Email Form -->
      <div
        class="bg-[#111a3e] w-full h-full rounded-xl overflow-hidden border border-[#111a3e] backdrop-blur p-6"
      >
        <form
          @submit.prevent="sendEmail"
          class="flex flex-col"
          data-aos="zoom-in-up"
        >
          <div class="mb-6">
            <label for="email" class="text-white block mb-2 text-sm font-medium"
              >Email</label
            >
            <input
              v-model="form.email"
              type="email"
              id="email"
              class="bg-[#111827] text-gray-100 text-sm rounded-lg block w-full p-2.5"
              placeholder="your-email@gmail.com"
              required
            />
          </div>
          <div class="mb-6">
            <label
              for="subject"
              class="text-white block mb-2 text-sm font-medium"
              >Subject</label
            >
            <input
              v-model="form.subject"
              type="text"
              id="subject"
              class="bg-[#111827] text-gray-100 text-sm rounded-lg block w-full p-2.5"
              placeholder="Subject"
              required
            />
          </div>
          <div class="mb-6">
            <label
              for="message"
              class="text-white block mb-2 text-sm font-medium"
              >Message</label
            >
            <textarea
              v-model="form.message"
              id="message"
              class="bg-[#111827] text-gray-100 text-sm rounded-lg block w-full p-2.5"
              placeholder="Let's talk about..."
              required
            ></textarea>
          </div>
          <button
            type="submit"
            class="w-full px-6 py-3 rounded-full text-white bg-primary border-2 border-transparent"
          >
            Send Message
          </button>
          <!-- Success/Error Message -->
          <p
            v-if="statusMessage"
            class="mt-4 text-center font-medium"
            :class="statusClass"
          >
            {{ statusMessage }}
          </p>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup>
  import { ref } from 'vue';
  import emailjs from 'emailjs-com';

  const form = ref({
    email: '',
    subject: '',
    message: '',
  });

  const statusMessage = ref('');
  const statusClass = ref('');

  const sendEmail = () => {
    emailjs
      .send(
        'service_pw7intd', // Replace with your EmailJS service ID
        'template_m1o6t3q', // Replace with your EmailJS template ID
        {
          email: form.value.email,
          subject: form.value.subject,
          message: form.value.message,
        },
        'WChYuM07tghr-vnBA' // Replace with your EmailJS user ID
      )
      .then(
        response => {
          statusMessage.value = '✅ Message sent successfully!';
          statusClass.value = 'text-green-500';
          setTimeout(() => (statusMessage.value = ''), 5000);
          form.value.email = '';
          form.value.subject = '';
          form.value.message = '';
        },
        error => {
          console.error(error);
          statusMessage.value =
            '❌ Error sending message. Please use a valid email.';
          statusClass.value = 'text-red-500';
        }
      );
  };
</script>
