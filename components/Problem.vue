<template>
  <div class="problem-card">
    <div class="problem">
      <h3 class="title">{{ problem }}</h3>
      <p class="text">{{ format_date(date) }}</p>
      <p class="text">{{ city }}, {{ country }}</p>
    </div>
    <div class="state">{{ state }}</div>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  methods: {
    format_date(value) {
      if (value) {
        return moment(value).format('MMMM Do YYYY, h:mm:ss a')
      }
    },
  },
  props: ['problem', 'date', 'city', 'country', 'state'],
}
</script>

<style>
.problem-card {
  cursor: pointer;
  transition: box-shadow 0.2s ease;
}

.problem-card:hover {
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.3);
}
.problem {
  padding: 10px;
}
.title {
  font-weight: bold;
  margin-bottom: 7px;
}

.text {
  color: rgb(182, 182, 182);
  margin-top: 0;
  margin-bottom: 0;
}

.state {
  border-top: 2px solid rgb(0, 126, 130);
  border-bottom: 2px solid rgb(0, 126, 130);
  padding: 5px 10px;
  font-weight: bold;
  color: rgb(0, 126, 130);
}
</style>
