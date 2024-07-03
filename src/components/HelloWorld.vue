<template>
  <v-container class="fill-height">
    <v-responsive
      class="align-centerfill-height mx-auto"
      max-width="900"
    >
      <v-row>
        <v-col cols="12">
          <h1>これって何時間？</h1>
        </v-col>
        <v-col cols="12">
          <h1>{{ sec2Hours(time) }}</h1>
        </v-col>
        <v-col cols="12">
          <v-text-field
            label="秒"
            variant="outlined"
            row-height="15"
            rows="1"
            v-model="time"
          ></v-text-field>
        </v-col>
      </v-row>
    </v-responsive>
  </v-container>
</template>

<script setup lang="ts">
  import { ref } from 'vue'

  const time = ref<number>(0)

  const sec2Hours = (seconds: number): string => {
    const day: number = Math.floor(seconds / 86400)
    const hour: number = Math.floor(seconds % 86400 / 3600)
    const min: number = Math.floor(seconds % 3600 / 60)
    const sec: number = seconds % 60
    let time = ''
    if(day !== 0) {
      time = `${day}日${hour}時間${min}分${sec}秒`;
    }else if(hour !==0 ) {
      time = `${hour}時間${min}分${sec}秒`;
    }else if(min !==0) {
      time = `${min}分${sec}秒`;
    }else {
      time = `${sec}秒`;
    }
    return time;
  }
</script>
<style>
body {
  font-family: 'NotoSans';
}
</style>