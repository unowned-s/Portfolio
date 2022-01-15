<template>
  <footer class="footer">
    <div class="container copyright">
      <span
        >© {{ new Date().getFullYear() }} {{ settings.site_name }}.co.in</span
      ><br />
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
</style>
