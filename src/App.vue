<template>
  <div id="app">
    <h3>Create New Data</h3>
    <FormToGoToServer @on-submit="submit" />
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios';
import FormToGoToServer from './components/FormToGoToServer.vue';

export default {
  name: 'App',
  components: {
    FormToGoToServer
  },
  data(){
    return {
      forcast: null
    }
  },
mounted(){
  axios
  .get('http://localhost:8080/forecast/Horsens')
  .then(response => console.log(response))
  .catch(error => console.log(error));
   axios
  .get('http://localhost:8080/forecast/Aarhus')
  .then(response => console.log(response))
  .catch(error => console.log(error));
   axios
  .get('http://localhost:8080/forecast/Copenhagen')
  .then(response => console.log(response))
  .catch(error => console.log(error));
  axios
  .post("http://localhost:8080/data", {/*params here*/})
},
methods:
{
   submit(){
          axios
            .post("http://localhost:8080/data",this.form)
            .then(function (response) {
				alert(response.statusText)
				console.log(response);
			})
			.catch(function (error) {
				console.log(error);
			});
      }
}

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
