<template>
  <div>
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
  border-top: 2px solid rgb(230, 230, 230);
  border-bottom: 2px solid rgb(230, 230, 230);
  padding: 5px 10px;
  cursor: pointer;
  transition: font-weight 0.1s ease;
}

.state:hover {
  font-weight: bold;
  color: rgb(0, 126, 130);
  border-top: 2px solid rgb(0, 126, 130);
  border-bottom: 2px solid rgb(0, 126, 130);
}
</style>
