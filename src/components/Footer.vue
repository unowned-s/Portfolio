<template>
  <footer class="footer">
    <div class="container copyright">
      <span>© {{ new Date().getFullYear() }} {{ settings.site_name }}.</span>
      <br>
      <small class="copylink">
      <g-link to="/terms">Terms of use</g-link> |
      <g-link to="/policy">Privacy policy</g-link> |
      <g-link to="/contact">Contact us</g-link>
    </small>
      <br>
      <small v-html="settings.footer" />
    </div>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      settings: require("../../data/theme.json")
    };
  }
};
</script>

<style scoped>
.footer {
  font-size: 1rem;
  padding: 6rem 0;
  text-decoration: none;
}
.copyright {
  margin: 0 auto;
  text-align: center;
}
.copylink {
  text-decoration: none;
  line-height: 2rem;
}

small {
  color: gray;
}
</style>
