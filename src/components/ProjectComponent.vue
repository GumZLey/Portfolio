<template>
  <section
    class="flex lg:flex-row justify-around items-center w-full min-h-[500px] p-10 xs:flex-col-reverse gap-10 xs:p-2"
    :class="ProjectData.id % 2 === 0 ? 'lg:flex-row-reverse' : 'lg:flex-row'"
  >
    <div class="flex flex-col justify-start items-start text-left gap-2">
      <h1 class="text-4xl font-bold mt-2 leading-15 ml-1">
        {{ ProjectData.name }}
      </h1>
      <article class="text-base mt-4 ml-1 max-w-[500px]">
        {{ ProjectData.description }}
      </article>
      <img
        src="@/assets/github.png"
        class="py-2 px-2 w-14 h-14 hover:text-primary transition-colors duration-300 text-primary/80 underline cursor-pointer"
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
  ProjectData: Object,
})

const imagePath = new URL(`../assets/${props.ProjectData.image}`, import.meta.url).href

const toGithub = () => {
  window.open(props.ProjectData.link, '_blank')
}
</script>
