<template>
  <div id="app">
    <Header />
    <div class="card">
      <router-view/>
    </div>
    <Footer />
  </div>
</template>

<script>
import Footer from './components/Footer';
import Header from './components/Header';

export default {
  components: {
    Footer,
    Header
  },
}
</script>


<style lang="scss">
#app {
  width: 100vw;
  overflow-x: hidden;
  margin: 0;
  padding: 0;
  font-family: 'Open Sans', sans-serif;

  i {
    cursor: pointer;
  }
}

.card {
  position: absolute;
  width: 75%;
  height: 50%;
  left: 12.5%;
  top: 25%;
  box-shadow: 0px 15px 35px rgba(50, 50, 93, 0.1), 0px 5px 15px rgba(0, 0, 0, 0.07);
  border-radius: 4px;
}
</style>
