<template>
  <div id="app">
    <Header></Header>
    <Counter></Counter>
    <Footer></Footer>
  </div>
</template>

<script>
import Header from "./components/header";
import Counter from "./components/counter";
import Footer from "./components/footer";

export default {
  name: "App",
  components: { Header, Counter, Footer },
};
</script>

<style>
html,
body {
  height: 100%;
  font-family: Arial, Helvetica, sans-serif;
}

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

#app {
  height: 100%;
  display: flex;
  flex-direction: column;
}
</style>
