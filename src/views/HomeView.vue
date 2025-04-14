<script setup>
import { HiChevronDoubleDown } from 'vue-icons-plus/hi'
import { ref, onMounted } from 'vue'
import ProjectComponent from '@/components/ProjectComponent.vue'
import ProjectComponentNoD from '@/components/ProjectComponentNoD.vue'

// Dynamically import all images from the skills folder
const skillImages = ref([])
const skillContext = import.meta.glob('@/assets/skills/*.{png,jpg,jpeg}', { eager: true })

const projects = ref([
  {
    id: 1,
    name: 'Image Segment Nothing',
    description:
      'This project is a web-based Deep-Learning integration that provides advanced image segmentation capabilities. Users can upload images, process them using AI-powered segmentation, visualize segmented regions, and download the results. MERN Stack (With no MongoDB)',
    image: 'SN.png',
    link: 'https://github.com/GumZLey/image-segment-nothing-project',
  },
  {
    id: 2,
    name: 'Contact List',
    description:
      'Contact List is a web app designed to make managing contacts simple and convenient. Users can securely log in with Google, then add, edit, delete, and search through their contact list. The frontend is built with Vue 3, Vuex for state management, and Tailwind CSS for styling. Axios handles API calls. The backend runs on Node.js with Express.js. MongoDB stores user and contact data. Security is handled with md5 for password hashing and dotenv for managing environment variables. Development tools like ESLint, Prettier keep the code clean and consistent.',
    image: 'Contact-List-Login.png',
    link: 'https://github.com/GumZLey/Contact-List',
  },
  {
    id: 3,
    name: 'Locus',
    description:
      'The Locus, project handles various game elements like players, projectiles, and objects, all while keeping the UI responsive. It’s built with Java and uses the Swing framework for graphical components like the game window, settings, credits, and a "how-to-play" guide. Sound effects and background music are added using Java’s javax.sound.sampled package. The code follows object-oriented principles, with classes like GameWindow, Player, and Projectile. The project is mainly focused on Thread.',
    image: 'Locus.png',
    link: 'https://github.com/GumZLey/Locus',
  },
  {
    id: 4,
    name: 'Agado (Ongoing)',
    description:
      "Agado is like an Agoda clone, but different. This website will collect data on the dormitory near Mahidol University and filter the best price value for the dormitory. I'll use Google Map API for the location, PostgreSQL for the database, Node Express for the backend, and Vue for the frontend. The seller can also list their place on the website.",
    image: 'Agado.png',
    link: 'https://github.com/GumZLey',
  },
  {
    id: 5,
    name: 'Dead Prevention (Ongoing)',
    description:
      "The Dead Prevention. In this project, We'll use an Embedded system to send the data shown in the card. We use Strapi as a backend data management and show data in Vue. This project will save patients who need help while waiting for a doctor. The products will attach to the finger of the patient to make the patient not feel uncomfortable.",
    image: 'Dead_Prevention.png',
    link: 'https://github.com/GumZLey',
  },
])

const projectImagesFM = ref([
  {
    id: 1,
    name: 'NFT preview card',
    image: 'nft-preview.png',
    link: 'https://github.com/GumZLey/nft-preview-card-component-main',
  },
  {
    id: 2,
    name: 'QR code component',
    image: 'QR.png',
    link: 'https://github.com/GumZLey/qr-code-component-Practice',
  },
  {
    id: 3,
    name: 'Result Summary',
    image: 'Result.png',
    link: 'https://github.com/GumZLey/FEM-Result_summary',
  },
])

const projectImagesODIN = ref([
  {
    id: 1,
    name: 'Calculator',
    image: 'Calculator.png',
    link: 'https://github.com/GumZLey/git_test/tree/main/Project/Calculator',
  },
  {
    id: 2,
    name: 'Dashboard',
    image: 'Dashboard.png',
    link: 'https://github.com/GumZLey/git_test/tree/main/Project/Dashboard',
  },
  {
    id: 3,
    name: 'Etch A Sketch',
    image: 'Etch.png',
    link: 'https://github.com/GumZLey/git_test/tree/main/Project/Etch-a-Sketch',
  },
  {
    id: 4,
    name: 'Library',
    image: 'Library.png',
    link: 'https://github.com/GumZLey/git_test/tree/main/Project/Library',
  },
  {
    id: 5,
    name: 'Sign up Form',
    image: 'Sign-up.png',
    link: 'https://github.com/GumZLey/git_test/tree/main/Project/Sign-up-Form',
  },
  {
    id: 6,
    name: 'Tic Tac Toe',
    image: 'Tic.png',
    link: 'https://github.com/GumZLey/git_test/tree/main/Project/Tic-Tac-Toe',
  },
  {
    id: 7,
    name: 'Landing Page',
    image: 'Landing.png',
    link: 'https://github.com/GumZLey/git_test/tree/main/Project/landing-page',
  },
  {
    id: 8,
    name: 'Recipes',
    image: 'Recipes.png',
    link: 'https://github.com/GumZLey/git_test/tree/main/Project/recipes',
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
  <header class="transition-all duration-700 ease-in-out translate-y-[-50px] opacity-0">
    <div class="wrapper font-Poppins">
      <nav class="flex justify-between items-center text-primary w-full px-20 py-6">
        <h1 class="font-knewave text-2xl">Ananda</h1>
        <div class="flex flex-row gap-8">
          <h2
            @click="scrollToSection('aboutSection')"
            class="cursor-pointer hover:-translate-y-1 duration-150"
          >
            About
          </h2>
          <h2
            @click="scrollToSection('projectsSection')"
            class="cursor-pointer hover:-translate-y-1 duration-150"
          >
            Projects
          </h2>
          <h2
            @click="scrollToSection('contactSection')"
            class="cursor-pointer hover:-translate-y-1 duration-150"
          >
            Contact
          </h2>
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
      <h1
        class="font-knewave text-black text-[160px] transition-all ease-in-out translate-y-[-70px] opacity-0 delay-700"
        id="myName"
      >
        ANANDA
      </h1>
      <div class="scroll-down flex flex-col justify-center items-center mt-20">
        <p class="text-secondary text-xl font-semibold animate-bounce">Scroll Down</p>
        <HiChevronDoubleDown class="animate-bounce text-black" size="36" />
      </div>
    </section>
    <section
      class="flex lg:flex-row justify-around items-center w-full min-h-[500px] p-10 mb-40 md:flex-col-reverse sm:flex-col-reverse"
      id="aboutSection"
    >
      <div class="flex flex-col justify-start items-start text-left gap-2">
        <h2 class="text-lg">Who am I</h2>
        <h1 class="text-4xl font-bold mt-2 leading-15 ml-1">
          Software <br />
          Engineer.
        </h1>
        <article class="text-base mt-4 ml-1">
          Full-stack developers can’t describe me the best. <br />
          I’ve experienced so many things in the past. Such as, <br />
          Machine Learning, Game Development, Web Development, <br />
          Platforms like LeetCode grinder, Embedded. But right now, <br />
          I want to focus on Web Development first.
        </article>
        <a
          class="mt-8 py-2 px-2 hover:text-primary transition-colors duration-300 text-primary/80 underline cursor-pointer"
          @click="scrollToSection('contactSection')"
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
    <section
      class="flex flex-col justify-start lg:items-center w-full min-h-[500px] p-10 bg-pink-bg mb-40 sm:items-center"
    >
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
    <section class="flex flex-col justify-start items-start w-full min-h-fit p-10 gap-10">
      <h1 class="text-4xl text-left ml-23">The Odin Project</h1>
      <div class="flex flex-row flex-wrap justify-center items-center gap-10">
        <div v-for="(project, index) in projectImagesODIN" :key="index" class="w-fit">
          <ProjectComponentNoD :ProjectDataNoD="project" />
        </div>
      </div>
    </section>
    <section class="flex flex-col justify-start items-start w-full min-h-fit p-10 gap-10">
      <h1 class="text-4xl text-left ml-23">Frontend Mentor</h1>
      <div class="flex flex-row flex-wrap justify-center items-center gap-10">
        <div v-for="(project, index) in projectImagesFM" :key="index" class="w-fit">
          <ProjectComponentNoD :ProjectDataNoD="project" />
        </div>
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
