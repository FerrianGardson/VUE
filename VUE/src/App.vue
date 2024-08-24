<template>
  <input type="text" v-model="userName" placeholder="Имя"></input>
  <input type="password" v-model="userPass" placeholder="Пароль"></input>
  <input type="email" v-model="userEmail" placeholder="Email"></input>
  <button @click="sendData()">Отправить</button>
  <p className="error"></p>
  <p>{{ users }}</p>
</template>

<style scoped>
h1 {
  color: red
}
</style>

<script>
export default {
  data() {
    return {
      users: [],
      userName: '',
      userPass: '',
      userEmail: '',
    }
  },
  methods: {
    sendData() {
      if (this.userName == '')
        this.error = 'Вбейте имя'
      return;
      if (this.userPass == '')
        this.error = 'Вбейте пароль'
      return;
      if (this.userEmail == '')
        this.error = 'Вбейте почту'
      return;

      this.users.push({
        name: this.userName,
        pass: this.userPass,
        emai: this.userEmail
      })
    }
  }
}
</script>