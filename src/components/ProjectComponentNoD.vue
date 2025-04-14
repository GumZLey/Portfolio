<template>
  <section
    class="flex xs:flex-col-reverse md:justify-around xs:justify-center items-center w-full min-h-[200px] md:p-10 xs:p-2"
  >
    <div class="flex flex-row justify-center items-center text-left gap-2">
      <h1 class="md:text-4xl xs:text-2xl font-bold mt-2 leading-15 ml-1">
        {{ ProjectDataNoD.name }}
      </h1>
      <img
        src="@/assets/github.png"
        class="py-2 px-2 w-14 h-14 mt-2 hover:text-primary transition-colors duration-300 text-primary/80 underline cursor-pointer"
        @click.prevent="toGithub"
        alt="Github"
      />
    </div>
    <div class="flex items-center justify-center">
      <img :src="imagePath" alt="My Profile" class="w-[600px] h-auto rounded-2xl object-cover" />
    </div>
  </section>
</template>

<script setup>
const props = defineProps({
  ProjectDataNoD: Object,
})

const imagePath = new URL(`../assets/${props.ProjectDataNoD.image}`, import.meta.url).href

const toGithub = () => {
  window.open(props.ProjectDataNoD.link, '_blank')
}
</script>
