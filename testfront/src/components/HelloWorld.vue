<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>This project created only for testing deploy</p>
    <p>Backend url: {{ getBackendUrl() }}</p>
    <div class="test-block">
      <p>{{ stringFromBackend }}</p>
      <input v-model="name" placeholder="Enter your name"><br>
      <button @click="send" :disabled="!(name.length > 0)">Send</button>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'HelloWorld',
    props: {
      msg: String
    },
    data() {
      return {
        stringFromBackend: '',
        name: '',
      }
    },
    methods: {
      async send () {
        try {
          const res = await axios.post('/graphql', {
              query: 'query test($name: String!) { test(name: $name ) }',
              variables: { name: this.name }
            })
          this.stringFromBackend = res.data.data.test
        } catch (e) {
          console.log('err', e)
        }
      },
      getBackendUrl() {
        return process.env.VUE_APP_BACKEND_URL
      }
    },
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

  .test-block {
    width: 300px;
    border: 1px solid #ccc;
    padding: 20px;
    margin: 10px auto;
  }
</style>
