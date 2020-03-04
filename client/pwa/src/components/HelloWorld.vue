<template>
  <div class="hello">
    <div class="container">
      <div class="row">
        <div class="col-sm-12" style="text-align: left">
          <b-button v-b-toggle.collapse-1 variant="primary">Filters</b-button>
        </div>
        <b-collapse id="collapse-1" class="mt-2">
          <div class="col-sm-12" v-for="(filter, key) in filters" v-bind:key="key" style="text-align: left;">
            <label>
              <div style="text-align: left"><strong>{{key}}</strong></div>
              <select class="form-control" v-model="querystring[key]">
                <option v-for="(option, key2) in filter" v-value="option" v-bind:key="key2">{{option}}</option>
              </select>
            </label>
          </div>
          <div class="col-sm-12" style="text-align: left">
            <b-button v-b-toggle.collapse-1 variant="success" v-on:click="getRecommendations()">Filter</b-button>
            <br />
            <br />
          </div>
        </b-collapse>
      </div>
      <div class="row">
        <div class="col-sm-12">
          <hr />
        </div>
      </div>
      <div class="row">
        <div class="col-sm-12" v-for="recommendation in recommendations" v-bind:key="recommendation">
          <b-card
                  :title="recommendation.model"
                  img-top
                  tag="article"
                  style="max-width: 20rem;"
                  class="mb-2"
          >
            <b-card-text>
              {{recommendation.details}}
            </b-card-text>
          </b-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import Vue from 'vue'
  import axios from 'axios'
  import VueAxios from 'vue-axios'
  const queryString = require('query-string');

  Vue.use(VueAxios, axios)

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {

  },
  data: function() {
    return {
      querystring: {},
      filters: {},
      recommendations: []
    }
  },
  methods: {
    getRecommendations: function(){
      Vue.axios.get(`http://127.0.0.1:5000/recommendations?${queryString.stringify(this.querystring)}`).then((response) => {
        this.recommendations = response.data;
      })
    }
  },
  mounted() {
    Vue.axios.get(`http://127.0.0.1:5000/filters`).then((response) => {
      this.filters = response.data;
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
