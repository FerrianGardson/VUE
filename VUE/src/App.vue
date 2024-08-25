<template>
  <input type="text" v-model="userName" placeholder="Имя" @keyup.enter="sendData" />
  <input type="password" v-model="userPass" placeholder="Пароль" @keyup.enter="sendData" />
  <input type="email" v-model="userEmail" placeholder="Email" @keyup.enter="sendData" />
  <button @click="sendData">Отправить</button>

  <!-- Исправления в условном рендеринге -->
  <div v-if="users.length === 0" class="elem">Нет пользователей</div>
  <div v-else-if="users.length === 1" class="elem">Один пользователь</div>
  <div v-else class="elem">Много пользователей</div>

  <div v-if="error" class="elem error">{{ error }}</div>
  <p>{{ users }}</p>

  <User v-for="(user, index) in users" :key="index" :user="user" :index="index" :deleteUser="deleteUser" />
</template>

<style scoped>
.error {
  color: red;
}

.elem {
  background: #f3f3f3;
  padding: 2rem;
  width: fit-content;
}
</style>

<script>
import User from "./components/User.vue";

export default {
  components: { User },
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
    },
    deleteUser(index) {
      this.users.splice(index, 1);
    }
  }
}
</script>
