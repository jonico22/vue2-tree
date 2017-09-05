<template>
  <div id="app">
    <ul>
      <item
        class="list"
        :model="treeData">
      </item>
    </ul>
  </div>
</template>

<script>
import item from './components/cTree.vue'
import axios from 'axios'

export default {
  name: 'app',
  data: () => ({
    treeData: []
  }),
  created() {
    axios.get(`./api.json`)
    .then(response => {
      // JSON responses are automatically parsed.
      this.treeData = response.data
      console.log(response.data);
    })
    .catch(e => {
      console.log(e);
      //this.errors.push(e)
    })
  },
  components: {
    item
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
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
.list{
  border-radius: .2rem;
  margin: 1rem .2rem;
  padding: 1rem;
  // background-color: red;
  display: block;
  // width: 100%;
  text-align: left;
}
</style>
