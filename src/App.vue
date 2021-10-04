<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div>gi</div>
    </v-app-bar>

    <v-main>
      <v-card>
        <east-light></east-light>
      </v-card>

      <v-row>
        <v-spacer></v-spacer>
        <v-col cols="6">
          <v-text-field
            v-model="getLabel"
          ></v-text-field>
        </v-col>
        <v-spacer></v-spacer>
      </v-row>
      
      <first-region
        @parse="getEvents"
      ></first-region>
    </v-main>
  </v-app>
</template>

<script>
import EastLight from './components/EastLight'
import FirstRegion from './components/FirstRegion'

export default {
  name: 'App',

  components: {
    EastLight,
    FirstRegion
  },

  data: () => ({
    events: [],
  }),
  computed: {
    getLabel() {
      let text = '';
      this.events.map(e => {
        text += e.name + " ";
      });
      return text;
    }
  },
  methods: {
    getEvents(event) {
      console.log(event);
      this.events = event
    },
  }
};
</script>
