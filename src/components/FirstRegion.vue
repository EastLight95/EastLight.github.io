<template>
  <v-card class="pa-4">
    <v-row no-gutters>
      <v-col cols="6">
        <v-btn class="ma-2" @click="bindTest">
            {{ getType }}
          <v-icon>add</v-icon>
        </v-btn>

        <v-btn class="ma-2" @click="refTest">
          ref
          <v-icon>search</v-icon>
        </v-btn>

        <v-btn class="ma-2" @click="makeEvent">
          이벤트 생성
          <v-icon>add</v-icon>
        </v-btn>

        <v-btn class="ma-2" @click="parseEvent">
          이벤트 보내기
          <v-icon>delete</v-icon>
        </v-btn>
      </v-col>

        <v-col cols="4">
          <v-select
            v-model="type"
            :items="item"
          ></v-select>
        </v-col>

        <v-col cols="2">
          <v-btn icon class="ma-2" @click="$refs.calendar.prev()">
            <v-icon>mdi-chevron-left</v-icon>
          </v-btn>
          <v-btn icon class="ma-2" @click="$refs.calendar.next()">
            <v-icon>mdi-chevron-right</v-icon>
          </v-btn>
        </v-col>
    </v-row>
    <v-row no-gutters>
      <v-col cols="12">
        <v-calendar
          v-model="value"
          ref="calendar"
          color="primary"
          :events="getEvents"
          :type="type"
          @click:event="eventClick"
          @click:date="dateClick"
        ></v-calendar>
      </v-col>
    </v-row>
  </v-card>
</template>

<script>
  export default {
    name: 'eastlight',

    data: () => ({
      value: '',
      item: ['month', 'week', '4day'],
      events: [],
      type: 'week',
      color: ['black', 'white', 'primary', 'grey']
    }),
    computed: {
      getType() {
        return this.type + ": function"
      },
      getEvents() {
        return this.events;
      },
      
    },
    watch: {
      value(newValue, oldValue) {
        console.log(newValue);
        console.log(oldValue);
      },
    },
    methods: {
      parseEvent() {
        this.$emit("parse", this.events);
      },
      refTest() {
        console.log(this.$refs.calendar);
      },
      dateClick() {
        console.log("date");
      },
      eventClick() {
        console.log("events");
      },
      bindTest() {
        this.type = "month"
      },
      makeEvent() {
        const day = "2021-10-0"
        const date = this.rnd(3, 9);
        // YYYY-MM-DD
        let time = day + date;
        const min = new Date(`${time}T00:00:00`)

        const firstTimestamp = min
        const first = new Date(firstTimestamp)
        this.events.push({
          name: "dong",
          start: first,
          color: this.color[3],
          timed: false,
        })
      },
      rnd (a, b) {
        return Math.floor((b - a + 1) * Math.random()) + a
      },
    },
  }
</script>
