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
      <div class="container">
        <div class="row">
          <div class="col-md">
            <h5>
              Prefixos
              <span class="badge bg-info">{{ prefixes.length }}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="prefix in prefixes"
                    :key="prefix"
                  >
                    <div class="row">
                      <div class="col-md">
                        {{ prefix }}
                      </div>
                      <div class="col-md text-end">
                        <button
                          class="btn btn-info"
                          v-on:click="deletePrefix(prefix)"
                        >
                          <span class="fa fa-trash"></span>
                        </button>
                      </div>
                    </div>
                  </li>
                </ul>
                <br />
                <div class="input-group">
                  <input
                    class="form-control"
                    type="text"
                    placeholder="Digite o prefixo"
                    v-model="prefix"
                    v-on:keyup.enter="addPrefix(prefix)"
                  />
                  <div class="input-group-append">
                    <button class="btn btn-info" v-on:click="addPrefix(prefix)">
                      <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-md">
            <h5>
              Sufixos
              <span class="badge bg-info">{{ prefixes.length }}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="sufix in sufixes"
                    :key="sufix"
                  >
                    <div class="row">
                      <div class="col-md">
                        {{ sufix }}
                      </div>
                      <div class="col-md text-end">
                        <button
                          class="btn btn-info"
                          v-on:click="deleteSufix(sufix)"
                        >
                          <span class="fa fa-trash"></span>
                        </button>
                      </div>
                    </div>
                  </li>
                </ul>
                <br />
                <div class="input-group">
                  <input
                    class="form-control"
                    type="text"
                    placeholder="Digite o sufixo"
                    v-model="sufix"
                    v-on:keyup.enter="addSufix(sufix)"
                  />
                  <div class="input-group-append">
                    <button class="btn btn-info" v-on:click="addSufix(sufix)">
                      <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <br />
        <h5>
          Domínios <span class="badge bg-info">{{ domains.length }}</span>
        </h5>
        <div class="card">
          <div class="card-body">
            <ul class="list-group">
              <li
                class="list-group-item"
                v-for="(domain, index) in domains"
                :key="index"
              >
                {{ domain }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";

export default {
  name: "App",
  data() {
    return {
      prefix: "",
      sufix: "",
      prefixes: [],
      sufixes: [],
      domains: [],
    };
  },
  methods: {
    addPrefix(prefix) {
      this.prefixes.push(prefix);
      this.prefix = "";
      this.generate();
    },
    deletePrefix(prefix) {
      this.prefixes.splice(this.prefixes.indexOf(prefix), 1);
      this.generate();
    },
    addSufix(sufix) {
      this.sufixes.push(sufix);
      this.sufix = "";
      this.generate();
    },
    deleteSufix(sufix) {
      this.sufixes.splice(this.sufixes.indexOf(sufix), 1);
      this.generate();
    },
    generate() {
      this.domains = [];
      for (const prefix of this.prefixes) {
        for (const sufix of this.sufixes) {
          this.domains.push(prefix + sufix);
        }
      }
    },
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
