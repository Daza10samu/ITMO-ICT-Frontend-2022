<template>
  <div class="login-box">
    <h2>Register</h2>
    <form type="submit" @submit.prevent="onRegSubmit">
      <div class="user-box">
        <input class="form-control" v-model="user.userName" type="text" name="name" autocomplete="off" required>
        <label>Username</label>
      </div>
      <div class="user-box">
        <input class="form-control" v-model="user.email" type="email" name="email" autocomplete="off" required>
        <label>Email</label>
      </div>
      <div class="user-box">
        <input class="form-control" v-model="user.password" type="password" name="password" autocomplete="off" required>
        <label>Password</label>
      </div>
      <div class="user-box">
        <input class="" type="password" name="" autocomplete="off" required>
        <label>Verify Password</label>
      </div>
      <div class="buttons-box">
        <button class="btn" type="submit">
          <span></span>
          <span></span>
          <span></span>
          <span></span>
          Submit
        </button>
        <button class="btn" @click="redirect">
          <span></span>
          <span></span>
          <span></span>
          <span></span>
          Login
        </button>
      </div>
    </form>
  </div>
</template>

<script>
import {mapActions} from 'pinia';
import useUsersStore from "@/stores/users";
import router from "@/router";

export default {
  data() {
    return {
      user: {
        userName: "",
        email: "",
        password: "",
        coins: [],
      },
      agree: false
    }
  },
  methods: {
    ...mapActions(useUsersStore, ['register']),

    async onRegSubmit() {
      await this.register(this.user);
    },

    redirect() {
      router.push('/')
    }
  },
  beforeMount() {
    localStorage.getItem('pinia_users') ? router.push('/personal') : router.push('/register')
  }
}
</script>

<style scoped>
template{
  margin: 0;
  padding: 0;
  font-family: sans-serif;
  background: var(--bg-color)
}

.login-box {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 400px;
  padding: 40px;
  transform: translate(-50%, -50%);
  background: var(--card-color);
  box-sizing: border-box;
  box-shadow: 0 15px 25px #00000099;
  border-radius: 50px;
}

.login-box h2 {
  margin: 0 0 30px;
  padding: 0;
  color: var(--text-color);
  text-align: center;
}

.login-box .user-box {
  position: relative;
}

.login-box .user-box input {
  width: 100%;
  padding: 10px 0;
  font-size: 16px;
  color: var(--text-color);
  margin-bottom: 30px;
  border: none;
  border-bottom: 1px solid var(--text-color);
  outline: none;
  background: transparent;
}

.login-box .user-box label {
  position: absolute;
  top: 0;
  left: 0;
  padding: 10px 0;
  font-size: 16px;
  color: var(--text-color);
  pointer-events: none;
  transition: .5s;
}

.login-box .user-box input:focus ~ label,
.login-box .user-box input:valid ~ label {
  top: -20px;
  left: 0;
  color: #03e9f4;
  font-size: 12px;
}

.buttons-box {
  display: flex;
  justify-content: space-between;
  color: var(--text-color);
}

.login-box form button {
  position: relative;
  display: inline-block;
  padding: 10px 20px;
  color: var(--button-color);
  font-size: 16px;
  text-decoration: none;
  text-transform: uppercase;
  overflow: hidden;
  transition: .5s;
  margin-top: 20px;
  letter-spacing: 4px;
  background-color: rgba(0,0,0,0);
  border-width: 0;
}

.login-box button:hover {
  background: var(--button-hover);
  color: var(--button-color);
  border-radius: 5px;
  box-shadow: 0 0 5px #03e9f4,
  0 0 25px #03e9f4,
  0 0 50px #03e9f4,
  0 0 100px #03e9f4;
}

.login-box button span {
  position: absolute;
  display: block;
}

.login-box button span:nth-child(1) {
  top: 0;
  left: -100%;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #03e9f4);
  animation: btn-anim1 1s linear infinite;
}

@keyframes btn-anim1 {
  0% {
    left: -100%;
  }
  50%, 100% {
    left: 100%;
  }
}

.login-box button span:nth-child(2) {
  top: -100%;
  right: 0;
  width: 2px;
  height: 100%;
  background: linear-gradient(180deg, transparent, #03e9f4);
  animation: btn-anim2 1s linear infinite;
  animation-delay: .25s
}

@keyframes btn-anim2 {
  0% {
    top: -100%;
  }
  50%, 100% {
    top: 100%;
  }
}

.login-box button span:nth-child(3) {
  bottom: 0;
  right: -100%;
  width: 100%;
  height: 2px;
  background: linear-gradient(270deg, transparent, #03e9f4);
  animation: btn-anim3 1s linear infinite;
  animation-delay: .5s
}

@keyframes btn-anim3 {
  0% {
    right: -100%;
  }
  50%, 100% {
    right: 100%;
  }
}

.login-box button span:nth-child(4) {
  bottom: -100%;
  left: 0;
  width: 2px;
  height: 100%;
  background: linear-gradient(360deg, transparent, #03e9f4);
  animation: btn-anim4 1s linear infinite;
  animation-delay: .75s
}

@keyframes btn-anim4 {
  0% {
    bottom: -100%;
  }
  50%, 100% {
    bottom: 100%;
  }
}
</style>