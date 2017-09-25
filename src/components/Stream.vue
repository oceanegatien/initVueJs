<template>
  <div>
    <form v-on:submit="getData">
      <label for="name">Entrer le nom du stream</label>
      <input id="name" type="text" name="streamName" v-model="streamName"/>
      <button type="submit">ok</button>

    </form>
    <div v-if="streamState === null">
      {{streamName}} est Offline
    </div>

    <div v-if="streamChoice !== null || streamChoice !== undefined">
      <!-- <ul id="v-for-object">
      <li v-for="value in object">{{value}}</li>
    </ul> -->

  </div>
  </div>



</template>

<script>
import axios from 'axios';

  export default {
    data(){
        return {
          baseURL: "https://api.twitch.tv/kraken/streams/",
          streamName: '',
          streamState: undefined,
          apiKey: "mykey",
          streamChoice: [],
          errors: [],
        }
    },
    methods: {
      getData: function(e){
        e.preventDefault();
        let stream = axios.get(`${this.baseURL}${this.streamName}?client_id=${this.apiKey}`)
        .then(res => res.data.stream)
        .catch(function (err) {
          console.log(err)
          return err.data.error;
        });

        stream.then(function(data) {
          if (data !== null || data !== undefined) {
            this.streamState = undefined;
            this.streamChoice.push(data);
          }else{
            this.streamState = data;
          }
        });
        // stream.catch(data => this.errors.push(data));

      }

    }
}



//token fu8eqxgyo9aa1zwd8p19i62k4bsny8
</script>
