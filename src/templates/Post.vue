<template>
  <Layout>
    <div class="px-7 md:px-14 pt-7 md:pt-14">
      <h1>{{ $page.post.title }}</h1>
      <div class="flex items-center -mt-10 ">
        <p class="text-gray-500 ">{{ $page.post.date }}</p>
      </div>
    </div>
    <article class="justify-end px-7 md:px-14 pb-7 md:pb-14 text-justify" v-html="$page.post.content" />
    <div id="comments" class="p-7 border-t border-gray-200"></div>
  </Layout>
</template>

<page-query>
query Post ($path: String!) {
  post: post (path: $path) {
    title
    date (format: "DD/MM/YYYY")
    content
  }
}
</page-query>

<script>
import SEO from '../mixins/SEO.vue';

export default {
  mixins: [SEO],
};
</script>

<style>
article img {
  @apply block m-auto;
}
</style>