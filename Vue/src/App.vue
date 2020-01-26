<template>
  <div id="app">
    <h1>News</h1>
    <Search
            @search="searchCity"
    />
    <List
            v-bind:obj="obj"/>
  </div>
</template>

<script>
  import List from "@/components/List";
  import Search from "@/components/Search";
  export default {
    name: 'app',
    data() {
      return {
        obj: [],
      }
    },
    methods: {
      searchCity(city){
        let url = 'https://api.reliefweb.int/v1/reports?appname=apidoc&filter[field]=' +
                'disaster.name&filter[value]="' + city +':%20Earthquake"&fields[include][]=disaster.name';
        let req = new Request(url);
        fetch(req)
                .then(response => response.json())
                .then((data) => {
                  // eslint-disable-next-line no-console
                  console.log(data.data);
                  for (let i = 0; i < data.data.length; i ++){
                    let testObj = {
                      title: '',
                      url: ''
                    };
                    testObj.title = data.data[i].fields.title;
                    testObj.url = data.data[i].fields.disaster[0].name;
                    this.obj.push(testObj)
                  }
                });
        // eslint-disable-next-line no-console
        console.log("Now", this.obj)
      }
    },
    components: {
      List,
      Search
    }
  }
  //
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>