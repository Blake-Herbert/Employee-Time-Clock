<template>
  <div>
    <h1>Clock In</h1>
    <input v-model="pin" placeholder="Enter PIN" type="number"/>
    <button @click="clockIn">Clock In</button>
    <p>{{ message }}</p>
  </div>
</template>

<script>
import api from '@/services/api';

export default {
  data() {
    return {
      pin: '',
      message: ''
    };
  },
  methods: {
    async clockIn() {
      try {
        const response = await api.clockIn(this.pin);
        this.message = response.data.message;
      } catch (error) {
        this.message = 'Error: ' + error.response.data;
      }
    }
  }
};
</script>
