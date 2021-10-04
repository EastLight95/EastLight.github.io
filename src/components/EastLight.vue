<template>
  <div>
    <v-btn @click="click">
      버튼
      <v-icon>delete</v-icon>
    </v-btn>
  </div>
</template>

<script>
  export default {
    name: 'eastlight',

    data: () => ({
      
    }),
    methods: {
      click() {
        console.log("click event");
      }
    },
  }
</script>
