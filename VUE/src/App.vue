<template>
  <input type="text" v-model="userName" placeholder="Имя" />
  <input type="password" v-model="userPass" placeholder="Пароль" />
  <input type="email" v-model="userEmail" placeholder="Email" />
  <button @click="sendData">Отправить</button>
  <p className="error">{{ error }}</p>
  <p>{{ users }}</p>

  <div v-for="(el, index) in users" :key="index">
    <h3>{{ el.name }}</h3>
    <p>{{ e.email }} — <b>{{ el.pass }}</b></p>
  </div>
</template>

<style scoped>
.error {
  color: red;
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
      error: '', // Добавлено поле для ошибок
    }
  },
  methods: {
    sendData() {
      // Логика проверки полей
      if (this.userName === '') {
        this.error = 'Вбейте имя';
        return; // Исправлено: теперь return внутри блока if
      }
      if (this.userPass === '') {
        this.error = 'Вбейте пароль';
        return;
      }
      if (this.userEmail === '') {
        this.error = 'Вбейте почту';
        return;
      }

      // Если все проверки пройдены, сбросить ошибку
      this.error = '';

      // Добавление пользователя в массив users
      this.users.push({
        name: this.userName,
        pass: this.userPass,
        email: this.userEmail // Исправлено имя поля на email
      });

      // Очистка полей после добавления пользователя
      this.userName = '';
      this.userPass = '';
      this.userEmail = '';
    }
  }
}
</script>
