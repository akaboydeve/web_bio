<template>
  <div class="flex flex-col items-start">
    <div class="grid">
      <h1 class="text-xl font-bold">Projects are made by me</h1>
      <div class="grid gap-3 sm:grid-cols-2 mt-2">
        <CardProject
          :project="project"
          v-for="(project, index) in projects"
          :key="`project-${index}`"
        />
      </div>
      <WidgetTechnologies class="mt-2" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      projects: [
        {
          title: '345 Launcher',
          image: 'https://i.vgy.me/4oVLsP.png',
          description: 'Lightweight and advanced Minecraft Launcher',
          link: 'https://github.com/mehmetali345dev/345-launcher',
        },
        {
          title: 'RepeatPay',
          image: 'https://repeatpay.ga/icon.png',
          description:
            'New open-source donate system for community. Easy, fast and secure.',
          link: 'https://repeatpay.ga',
        },
        {
          title: 'This website',
          image: 'https://345dev.me/icon.png',
          description: 'My personal portfolio made with NuxtJS and WindiCSS',
          link: '/',
        },
        {
          title: 'MADE',
          image: 'https://made.345dev.me/icon.png',
          description:
            "Awesome showcase for dotfiles and a wiki for ricing and for intruducing WM/DE's and ricing releated software to new users.",
          link: 'https://made.345dev.me',
        },
      ],
    }
  },
  computed: {
    getProjects() {
      return {
        featured: this.projects?.slice(0, 3),
        rest: this.projects.slice(3),
      }
    },
  },
  head() {
    const title = 'Projects'
    const description = 'You can see my projects and works from here.'
    const href = `https://345dev.me/info/projects`
    const object = {
      title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: description,
        },
        {
          hid: 'keywords',
          name: 'keywords',
          content: `mehmetali345, mehmetali345 blog, blog, teknoloji, vue, yaz??l??m, discord, mehmetali_345, g??nderi`,
        },
        // Open-Graph
        {
          hid: 'og:title',
          name: 'og:title',
          content: title,
        },
        {
          hid: 'og:description',
          name: 'og:description',
          content: description,
        },
        {
          hid: 'og:url',
          name: 'og:url',
          content: href,
        },
        // Twitter
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: title,
        },
        {
          hid: 'twitter:description',
          name: 'twitter:description',
          content: description,
        },
      ].map((i) => {
        if (i.name && !i.property) i.property = i.name
        return i
      }),
      link: [
        {
          rel: 'canonical',
          href,
        },
      ],
    }
    return object
  },
}
</script>

<style></style>
