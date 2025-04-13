<script setup>
import { HiChevronDoubleDown } from 'vue-icons-plus/hi'
import { ref, onMounted } from 'vue'
import ProjectComponent from '@/components/ProjectComponent.vue'

// Dynamically import all images from the skills folder
const skillImages = ref([])
const skillContext = import.meta.glob('@/assets/skills/*.{png,jpg,jpeg}', { eager: true })

const projects = ref([
  {
    id: 1,
    name: 'Image Segment Nothing',
    description: 'This project is a web-based Deep-Learning integration that provides advanced image segmentation capabilities. Users can upload images, process them using AI-powered segmentation, visualize segmented regions, and download the results.',
    image: '/assets/SN.png',
    link: 'https://github.com/GumZLey/image-segment-nothing-project',
  },
  {
    id: 2,
    name: 'Contact List',
    description: 'Contact List is a web app designed to make managing contacts simple and convenient. Users can securely log in with Google, then add, edit, delete, and search through their contact list. The frontend is built with Vue 3, Vuex for state management, and Tailwind CSS for styling. Axios handles API calls. The backend runs on Node.js with Express.js. MongoDB stores user and contact data. Security is handled with md5 for password hashing and dotenv for managing environment variables. Development tools like ESLint, Prettier keep the code clean and consistent.',
    image: '/assets/Contact-List-Login.png',
    link: 'https://github.com/GumZLey/Contact-List',
  },
])

for (const path in skillContext) {
  const fileName = path.split('/').pop().split('.')[0] // Extract file name without extension
  skillImages.value.push({
    src: skillContext[path].default || path, // Use default export if available
    name: fileName.charAt(0).toUpperCase() + fileName.slice(1), // Capitalize the name
  })
}

const toGoogleDrive = () => {
  window.open(
    'https://drive.google.com/drive/folders/1-5pJBW3yjcf6OWomnPjFRa_s9wt4g7ql?usp=sharing',
    '_blank',
  )
}

const toGithub = () => {
  window.open('https://github.com/GumZLey', '_blank')
}
const toInstagram = () => {
  window.open('https://www.instagram.com/ley_adk?igsh=Ymxoa2FkeXQ5dXVm&utm_source=qr', '_blank')
}
const toFacebook = () => {
  window.open('https://www.facebook.com/share/168vFHTEnu/?mibextid=wwXIfr', '_blank')
}
const toLinkedIn = () => {
  window.open('https://www.linkedin.com/in/ananda-kongkoed-862154217/', '_blank')
}
// Scroll to the specified section
const scrollToSection = (sectionId) => {
  const section = document.getElementById(sectionId)
  section?.scrollIntoView({ behavior: 'smooth' })
}

const handleScroll = () => {
  const sections = document.querySelectorAll('section')
  const header = document.querySelector('header')
  const myName = document.getElementById('myName')
  sections.forEach((section) => {
    const rect = section.getBoundingClientRect()
    if (rect.top < window.innerHeight && rect.bottom >= 0) {
      section.style.opacity = 1
      section.style.transform = 'translateY(0)'
      section.style.transitionDuration = '1500ms'
      section.style.transitionDelay = '300ms'
    } else {
      section.style.opacity = 0
      section.style.transform = 'translateY(-50px)'
      section.style.transitionDuration = '1500ms'
      section.style.transitionDelay = '300ms'
    }
  })
  header.style.opacity = 1
  header.style.transform = 'translateY(50px)'

  myName.style.opacity = 1
  myName.style.transform = 'translateY(70px)'
  myName.style.transitionDuration = '1500ms'
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  handleScroll() // Run initially to check visible sections
})
</script>

<template>
  <header class=" transition-all duration-700 ease-in-out translate-y-[-50px] opacity-0">
    <div class="wrapper font-Poppins">
      <nav class="flex justify-between items-center text-primary w-full px-20 py-6 ">
        <h1 class="font-knewave text-2xl">Ananda</h1>
        <div class="flex flex-row gap-8">
          <h2 @click="scrollToSection('aboutSection')" class="cursor-pointer">About</h2>
          <h2 @click="scrollToSection('projectsSection')" class="cursor-pointer">Projects</h2>
          <h2 @click="scrollToSection('contactSection')" class="cursor-pointer">Contact</h2>
        </div>
      </nav>
    </div>
  </header>

  <main class="font-Poppins font-semibold text-secondary">
    <section
      class="text-center text-secondary w-full h-screen flex flex-col justify-center items-center pb-30"
    >
      <p>
        Third-year University student at Mahidol University Full-stack Developer <br />
        No one hires me. So, I have to make this website.
      </p>
      <h1 class="font-knewave text-black text-[160px] transition-all ease-in-out translate-y-[-70px] opacity-0 delay-700" id="myName">ANANDA</h1>
      <div class="scroll-down flex flex-col justify-center items-center mt-20">
        <p class="text-secondary text-xl font-semibold animate-bounce">Scroll Down</p>
        <HiChevronDoubleDown class="animate-bounce text-black" size="36" />
      </div>
    </section>
    <section
      class="flex flex-row justify-around items-center w-full min-h-[500px] p-10 mb-40"
      id="aboutSection"
    >
      <div class="flex flex-col justify-start items-start text-left gap-2">
        <h2 class="text-lg">Who am I</h2>
        <h1 class="text-4xl font-bold mt-2 leading-15 ml-1">
          Software <br />
          Engineer.
        </h1>
        <article class="text-base mt-4 ml-1">
          Full-stack Developer can’t describe me the best. <br />
          I’m experiencing so many things in the past such as, <br />
          Machine Learning, Game Development, Web Development, <br />
          Platform like LeetCode grinder, Embedded. But right now, <br />
          I want to focusing on Web Development firsts.
        </article>
        <a
          href="#"
          class="mt-8 py-2 px-2 hover:text-primary transition-colors duration-300 text-primary/80 underline"
          >Contact Me</a
        >
      </div>
      <div class="flex items-center justify-center">
        <img
          src="@/assets/Ley_Profile.jpg"
          alt="My Profile"
          class="w-[400px] h-[400px] rounded-full object-cover"
        />
      </div>
    </section>
    <section class="flex flex-col justify-start items-start w-full min-h-[500px] p-10 bg-pink-bg mb-40">
      <h1 class="text-4xl font-bold mb-10 ml-23">Skills</h1>
      <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-7 gap-20">
        <div
          v-for="(skill, index) in skillImages"
          :key="index"
          class="flex flex-col justify-start items-center text-center gap-2"
          :class="[index % 2 === 0 ? 'mt-10' : 'mb-10', index % 3 === 0 ? 'mt-15' : 'mb-15']"
        >
          <img
            :src="skill.src"
            :alt="skill.name"
            class="w-20 h-20 object-contain"
            :class="[
              index % 2 === 0
                ? 'animate-[bounce_1.5s_infinite]'
                : 'animate-[bounce_1.75s_infinite]',
              index % 3 === 0 ? 'animate-[bounce_2s_infinite]' : 'animate-[bounce_1.5s_infinite]',
              skill.name === 'Java' ? 'w-40 h-40' : '',
            ]"
          />
        </div>
      </div>
    </section>
    <section
      class="flex flex-col justify-start items-start w-full min-h-fit p-10 gap-10"
      id="projectsSection"
    >
      <h1 class="text-4xl text-left ml-23">Projects</h1>
      <div v-for="(project, index) in projects" :key="index" class="w-full">
        <ProjectComponent :ProjectData="project" />
      </div>
    </section>

    <footer
      class="flex flex-col justify-start items-center w-full min-h-[300px] p-10 gap-10 bg-dark-bg"
      id="contactSection"
    >
      <h1 class="text-4xl text-primary font-bold">Start Hiring Me</h1>
      <div class="flex flex-row justify-between items-center gap-10 w-[80%] mt-6">
        <div class="flex flex-col justify-start items-start text-left gap-2">
          <h1>kliv2554@gmail.com</h1>
          <h1>089-929-3799</h1>
        </div>
        <div class="flex flex-col justify-center items-center text-left gap-2">
          <a @click="toGoogleDrive" class="cursor-pointer underline"
            >Click Here to download my CV</a
          >
          <div class="flex flex-row justify-center items-center gap-2">
            <img
              src="@/assets/Socials/Instagram.png"
              alt="Instagram"
              class="w-10 h-10 cursor-pointer transition-transform duration-300 ease-in-out hover:-translate-y-1"
              @click="toInstagram"
            />
            <img
              src="@/assets/Socials/Facebook.png"
              alt="Facebook"
              class="w-10 h-10 cursor-pointer transition-transform duration-300 ease-in-out hover:-translate-y-1"
              @click="toFacebook"
            />
            <img
              src="@/assets/Socials/Github.png"
              alt="Github"
              class="w-10 h-10 cursor-pointer transition-transform duration-300 ease-in-out hover:-translate-y-1"
              @click="toGithub"
            />
            <img
              src="@/assets/Socials/LinkedIn.png"
              alt="LinkedIn"
              class="w-10 h-10 cursor-pointer transition-transform duration-300 ease-in-out hover:-translate-y-1"
              @click="toLinkedIn"
            />
          </div>
        </div>
        <h1>
          Mahidol University <br />
          Third-year student
        </h1>
      </div>
    </footer>
  </main>
</template>

<style lang="css" scoped>
@keyframes headerDrop {
  0% {
    transform: translateY(-100%);
    opacity: 0;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
}

.animate-headerDrop {
  animation: headerDrop 1s forwards;
}
</style>
