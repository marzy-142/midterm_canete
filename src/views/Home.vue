<template>
  <div class="home-container">
    <h1 class="title">Welcome</h1>
    <nav class="nav">
      <router-link to="/home" class="nav-link">Home</router-link>
      <span class="nav-separator">|</span>
      <router-link to="/products" class="nav-link">Products</router-link>
    </nav>
    <div class="info">
      <p>Your Name: <strong>Mariella Canete</strong></p>
      <p>Program: <strong>Information Technology</strong></p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
}
</script>

<style scoped>
.home-container {
  background: linear-gradient(135deg, #1e1e2f, #2a2a45);
  color: #ffffff;
  font-family: 'Roboto', sans-serif;
  padding: 40px;
  border-radius: 15px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
}

.title {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 20px;
}

.nav {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.nav-link {
  color: #4db8ff;
  text-decoration: none;
  font-size: 1.2rem;
  margin: 0 10px;
  transition: color 0.3s;
}

.nav-link:hover {
  color: #80c8ff;
}

.nav-separator {
  color: #ffffff;
}

.info {
  text-align: center;
  font-size: 1.2rem;
}
</style>
