<template>
  <div class="d-flex justify-space-between align-center" style="width: 100%">
    <div>
      <a href="/">
        <img src="../assets/giphy-logo.png" alt="Giphy Logo" class="logo" />
      </a>
    </div>

    <div>
      <a href="#" class="login-button">
        <div class="icon-container">
          <v-icon color="#fff">
            person
          </v-icon>
        </div>
        <div class="text-container" style="">Log In</div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navbar',

  data: () => ({}),
};
</script>

<style scoped>
img.logo {
  height: 40px;
}
.login-button {
  background-color: #3e3e3e;
  padding: 0.6rem;
}
.login-button > .icon-container {
  display: inline-block;
  padding: 0 0.2rem;
}
.login-button > .text-container {
  display: inline-block;
  height: 100%;
  padding: 0 2rem;
  color: #fff;
  font-weight: 500;
  font-size: 14px;
}
</style>
