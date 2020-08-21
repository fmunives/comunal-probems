<template>
  <div class="container problems-container">
    <div class="box-shadow problems">
      <!-- TODO click to go message details -->
      <div v-for="problem of problems">
        <Problem
          :problem="problem.problem_type.name"
          :date="problem.created_at"
          :city="problem.location.city.name"
          :country="problem.location.city.timeZone"
          :state="problem.problem_state.name"
        />
      </div>
    </div>
    <div class="box-shadow messages">
      <div class="message-content"></div>
      <input
        class="message-input"
        type="text"
        placeholder="escribe tu mensaje aquí"
      />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      problems: [],
    }
  },
  created() {
    let token =
      'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiZGVmYXVsdCIsImlzX2NvbXVuYWwiOmZhbHNlLCJpc3MiOiJ0ZXN0LmNvbXVuYWxjb3dvcmtpbmcuY29tIiwiaGFzX3BlbmRpbmdfaW52aXRhdGlvbiI6ZmFsc2UsImxvY2F0aW9uX2lkIjoibG9faWk0NTRpQUo1RjdEUTBwdCIsImhhc19mdWxsX3Byb2ZpbGUiOnRydWUsImJ1c2luZXNzX3R5cGUiOiJjb3dvcmtpbmciLCJleHAiOjE2Mjk1ODAxNzksInVzZXIiOiJ1c19FejRURHJUQzRxRGxxaGliIiwiYnVzaW5lc3NfaWQiOiJjb211bmFsX2Nvd29ya2luZyIsImlhdCI6MTU5ODA0NDE3OSwib3V0bG9va19zeW5jZWQiOmZhbHNlLCJqdGkiOiJzZV9va0xBbGV5eDBkbzdPdUxZIn0.EiSOOQDoaIu-8Lqa6cblgNDYF_KMqGDSdWEvrcJfKSk'
    const endpoint = 'https://api-test.comunal.co'
    axios
      .get(`${endpoint}/problem`, {
        headers: {
          Authorization: 'Bearer ' + token,
          'Access-Control-Allow-Origin': '*',
        },
      })
      .then((response) => {
        this.problems = response.data.data
        console.log('problems', this.problems)
      })
  },
}
</script>

<style>
.problems-container {
  padding: 30px 0;
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
}

.problems,
.messages {
  border-radius: 10px;
  padding: 15px;
  background-color: #fff;
}

.problems {
  padding: 0;
}

.messages {
  display: flex;
  flex-direction: column;
}

.message-content {
  flex-grow: 1;
}

.message-input {
  padding: 5px 10px;
  border: 1px solid #ccc;
  outline: none;
  border-radius: 3px;
}

@media (min-width: 768px) {
  .problems-container {
    grid-template-columns: 1fr 2fr;
  }
}
@media (min-width: 992px) {
  .problems-container {
    grid-template-columns: 1fr 3fr;
  }
}
</style>
