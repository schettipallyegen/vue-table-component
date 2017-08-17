<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <table-component :table-data="league" :table-headers="leagueHeaders"></table-component>
  
    <form>
      <label>Hero Name</label>
      <input type="text" name="heroName" v-model="newLeagueMember.heroName" required>
      <label>Actual Name</label>
      <input type="text" name="actualName" v-model="newLeagueMember.actualName" required>
      <button type="submit" @click.prevent="addLeagueMember">Add</button>
    </form>
  
  </div>
</template>

<script>
  import TableComponent from './components/TableComponent.vue'
  import _ from 'lodash';
  
  const resetNewLeagueMember = {
    heroName: '',
    actualName: ''
  }
  
  export default {
    name: 'app',
    components: {
      TableComponent
    },
    data() {
      return {
        newLeagueMember: {
          heroName: '',
          actualName: ''
        },
        msg: `Let's look at our first Component`,
        leagueHeaders: ['Hero Name', 'Actual Name'],
        league: [{
          heroName: 'Batman',
          actualName: 'Bruce Wayne'
        }, {
          heroName: 'Wonder Women',
          actualName: 'Princess Diana'
        }, {
          heroName: 'Aquaman',
          actualName: 'Arthur Curry'
        }, {
          heroName: 'Cyborg',
          actualName: 'Victor Stone'
        }]
      }
    },
    methods: {
      addLeagueMember() {
        if (_.isEmpty(this.newLeagueMember.heroName) || _.isEmpty(this.newLeagueMember.actualName)) {
          alert('Please fill in the names correctly');
        } else {
          this.league.push(this.newLeagueMember);
          _.set(this, ['newLeagueMember'], _.cloneDeep(resetNewLeagueMember));
        }
      }
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
  
  h1,
  h2 {
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
</style>
