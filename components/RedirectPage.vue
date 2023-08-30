<template>
  <div>
    <!-- Your static page content here -->
  </div>
</template>

<script>
export default {
  created() {
    const referer = document.referrer;
    const queryParams = new URLSearchParams(window.location.search);

    if (this.isFacebookReferer(referer) || queryParams.has('fbclid')) {
      // Redirect to a different page
      window.location.href = 'https://nailsforus.com';
    }
  },
  methods: {
    isFacebookReferer(referer) {
      return referer.includes('facebook.com');
    }
  }
};
</script>
