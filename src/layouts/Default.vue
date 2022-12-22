<template>
  <div class="prose dark:prose-light md:container md:mx-auto md:px-48 ">
    <header
      class="px-7 flex justify-between items-center border-b md:border border-gray-200">
      <g-link to="/">
        <p>{{ $static.metadata.siteName }}</p>
      </g-link>
      <div class="flex items-center">
        <theme-switcher class="mr-4" />
        <g-link to="/">
          <p class="mr-4">Sobre</p>
        </g-link>
        <g-link to="/posts/">
          <p>Postagens</p>
        </g-link>
      </div>
    </header>
    <div class="md:border-r md:border-l md:border-gray-200 text-justify">
      <slot />
    </div>
    <footer
      class="text-sm px-7 flex items-center border-t md:border border-gray-200 text-center">
      <p class="text-center">ⓒ {{ currentYear }}. Rafael Begnini de Castilhos</p>
    </footer>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
    siteDescription
    siteUrl
  }
}
</static-query>

<script>
import ThemeSwitcher from '../components/ThemeSwitcher';

export default {
  components: {
    ThemeSwitcher,
  },
  data() {
    return {
      currentYear: new Date().getFullYear(),
    };
  },
  metaInfo() {
    return {
      meta: [
        {
          key: 'author',
          name: 'author',
          content: 'Rafael Begnini de Castilhos',
        },
      ],
    };
  },
};
</script>

<style>
@import url(http://fonts.googleapis.com/earlyaccess/notosanskr.css);

body {
  @apply dark:bg-gray-800;
  font-family: 'Noto Sans KR', -apple-system, system-ui, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
}

header a {
  @apply no-underline !important;
}
</style>
