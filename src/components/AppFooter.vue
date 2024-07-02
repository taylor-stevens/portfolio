<template>
    <v-footer height="40" app>
      <a
        v-for="info in socialMedia"
        :key="info.title"
        :href="info.href"
        :title="info.title"
        class="d-inline-block mx-2 social-link"
        rel="noopener noreferrer"
        target="_blank"
      >
        <v-icon
          :icon="info.icon"
          :size="24"
          style="color: white;"
        />
      </a>
      <div
        class="text-caption text-disabled"
        style="position: absolute; right: 16px;"
      >
        &copy; 2023-{{ (new Date()).getFullYear() }}
        —
        <a
          class="text-decoration-none on-surface"
          href="https://github.com/vuetifyjs/vuetify/blob/master/LICENSE.md"
          rel="noopener noreferrer"
          target="_blank"
        >
          MIT License
        </a>
      </div>
    </v-footer>
  </template>
  
  <script setup>
    
    // this will make buttons to acceess silvias social media in the footer
    const socialMedia = [
      {
        title: 'LinkedIn',
        icon: `fa-brands fa-linkedin-in`,
        href: 'https://www.linkedin.com/in/taylor-a-stevens/',
      },
      {
        title: 'Instagram',
        icon: 'fa-brands fa-instagram',
        href: 'https://www.instagram.com/taylor_stevenss/',
      },
      {
        title: 'Github',
        icon: 'fa-brands fa-github',
        href: 'https://github.com/taylor-stevens'
      },
      {
        title: 'Email',
        icon: 'fa-solid fa-envelope',
        href: 'mailto:taylorstevens14562@gmail.com'
      }
    ]
  </script>
  
  <style scoped lang="sass">
    .social-link :deep(.v-icon)
      color: rgba(var(--v-theme-on-background), var(--v-disabled-opacity))
      text-decoration: none
      transition: .2s ease-in-out
  
      &:hover
        color: rgba(25, 118, 210, 1)
  </style>