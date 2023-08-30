<template>
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

