<template>
  <div>
    <div id="slogan" class="text-center">
      <h1>NameGenerator</h1>
      <br />
      <h6 class="text-secondary">
        Gerador de nomes utilizando Vue.js, GraphQL e Node
      </h6>
    </div>
    <div id="main">
      <DomainList></DomainList>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";
import DomainList from "./components/DomainList";

export default {
  name: "App",
  components: {
    DomainList,
  },
};
</script>

<style>
.fa {
  color: white;
}

#slogan {
  margin-top: 30px;
  margin-bottom: 30px;
}

#main {
  background: #f1f1f1;
  padding-top: 30px;
  padding-bottom: 30px;
}
</style>
