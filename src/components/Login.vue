<template>
  
<div id="login">
  <div class="fullscreen-video-wrap">
    <video src="@/assets/cloud2.mp4" autoplay="" loop=""></video>
  </div>
  <div class="login-form-wrapper">
    <div class="login-wrapper" v-show="!alreadySignIn">
      <transition name="left-panel">
        <div class="form-bg" v-if="!login"></div>
      </transition>
      <transition name="transition-left">
        <div class="form-container" v-if="!login">
          <form class="form" @submit.prevent="">
            <h3 class="login-title">Sign In</h3>
            <input class="form-input" v-model="username" type="email" placeholder="Name"/>
            <input class="form-input" v-model="password" type="password" placeholder="Password"/>
            <button class="form-btn" v-on:click="signIn">SIGN IN</button>
          </form>
        </div>
      </transition>
    </div>
    <div class="login-wrapper">
      <transition name="transition-right">
        <div class="form-bg" v-if="login"></div>
      </transition>
      <transition name="transition-to-right">
        <div class="form-container" v-if="login">
          <form class="form" @submit.prevent="">
            <h3 class="login-title">Create Account</h3>
            <input class="form-input" type="text" placeholder="Name"/>
            <input class="form-input" type="text" placeholder="Email"/>
            <input class="form-input" type="password" placeholder="Password"/>
            <button class="form-btn">SIGN UP</button>
          </form>
        </div>
      </transition>
    </div>
    <div v-show="!alreadySignIn" class="form-aside" :class="{'form-aside-right': !login}">
      <transition name="transition-opacity">
        <div class="form-aside-signup" v-if="!login">
          <h2 class="login-title">Hello</h2>
          <p class="login-text">Please sign up</p>
          <button class="form-btn" @click="login = !login">SIGN UP</button>
        </div>
      </transition>
      <transition name="transition-opacity">
        <div class="form-aside-signin" v-if="login">
          <h2 class="login-title">Welcome Back</h2>
          <p class="login-text">If you already registered. Please sign in</p>
          <button class="form-btn" @click="login = !login">SIGN IN</button>
        </div>
      </transition>
    </div>
    <div v-show="alreadySignIn" class="form-center">
      <transition name="transition-opacity">
        <div class="form-aside-signup" v-if="!login">
          <h2 class="login-title">Welcome</h2>
          <p class="login-text">{{username}}</p>
          <button class="form-btn" @click="goback">Go Back</button>
        </div>
      </transition>
    </div>
  </div>
</div>

</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      login: false,
      alreadySignIn: false,
      username: '',
      password: ''
    }
  },
  methods: {
    signIn: function (e) {
      e.preventDefault();

      if (this.username && this.password) {
        this.alreadySignIn = true;
      }
      
    },
    goback: function() {
      this.alreadySignIn = false;
      this.username = '';
      this.password = '';
    }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,600,800");

#login {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100vw;
  min-height: 100vh;
}
.fullscreen-video-wrap{
    position:absolute;
    top:0;
    left:0;
    width:100%;
    height:100vh;
    overflow:hidden;
  }
.fullscreen-video-wrap video{
    min-height:100%;
    min-width:100%;
  }
.login-form-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  min-width: 800px;
  height: 475px;
  border-radius: 8px;
  box-shadow: 0 0 25px 0 rgba(41, 38, 33, 0.3);
  background-color: rgba(41, 38, 33, 0.5);
  overflow: hidden;
}

.form {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  color: #EFECE6;
}

.login-title {
  font-size: 35px;
}
.login-text {
  font-size: 15px;
  font-weight: 600;
}

.form__subtext {
  font-size: 13px;
  font-weight: 400;
}
.form-input {
  width: 100%;
  width: 250px;
  margin-bottom: 10px;
  padding: 10px 35px;
  border: none;
  border-bottom: 1px solid #787673;
  text-align: center;
  color: #EFECE6;
  background-color: transparent;
  outline: none;
}
.form-input:last-of-type {
  margin-bottom: 15px;
}
.form-btn {
  transition: 1.4s cubic-bezier(0.19, 1, 0.22, 1);
  display: block;
  margin: 0 auto;
  border: none;
  border-radius: 40px;
  padding: 13px 40px;
  font-size: 12px;
  font-weight: 600;
  color: #EFECE6;
  background-color: #F85A3E;
  outline: none;
  cursor: pointer;
}
.form-btn:active {
  -webkit-transform: scale(0.8);
          transform: scale(0.8);
}
.form-container {
  display: flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 10;
  width: 100%;
  height: 100%;
}
.form-bg {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 5;
  width: 100%;
  height: 100%;
  background-color: #292621;
  will-change: transform;
}
.login-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  width: 50%;
  height: 100%;
}
.form-aside {
  display: flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  top: 0;
  left: 0;
  transition: 1.4s cubic-bezier(0.19, 1, 0.22, 1);
  flex-direction: column;
  width: 50%;
  height: 100%;
  color: #EFECE6;
}

.form-center {
  left: 25%;
}

.form-aside-right {
  left: 50%;
}
.form-aside-signup, .form-aside-signin {
  display: flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  top: 0;
  left: 0;
  flex-direction: column;
  width: 100%;
  height: 100%;
  padding: 40px 40px 40px 0px;
}

.left-panel-enter, .left-panel-leave-to, .transition-right-enter, .transition-right-leave-to {
  z-index: 0;
}
.left-panel-leave, .left-panel-enter-to, .transition-right-leave, .transition-right-enter-to {
  z-index: 5;
  -webkit-transform: translateX(0);
          transform: translateX(0);
}
.left-panel-enter-active, .left-panel-leave-active, .transition-right-enter-active, .transition-right-leave-active {
  transition: 1.4s cubic-bezier(0.19, 1, 0.22, 1);
}
.left-panel-enter, .left-panel-leave-to {
  -webkit-transform: translateX(150%);
          transform: translateX(150%);
}
.transition-right-enter, .transition-right-leave-to {
  -webkit-transform: translateX(-150%);
          transform: translateX(-150%);
}
.transition-left-enter, .transition-to-right-enter {
  opacity: 0;
}
.transition-left-leave-to, .transition-to-right-leave-to {
  opacity: 0;
}
.transition-left-leave, .transition-left-enter-to, .transition-to-right-leave, .transition-to-right-enter-to {
  opacity: 1;
  -webkit-transform: translateX(0);
          transform: translateX(0);
}
.transition-left-enter-active, .transition-to-right-enter-active {
  transition: 1.4s cubic-bezier(0.19, 1, 0.22, 1), opacity 0.7s;
  transition-delay: 0.15s;
}
.transition-left-leave-active, .transition-to-right-leave-active {
  transition: 1.4s cubic-bezier(0.19, 1, 0.22, 1);
}
.transition-left-enter {
  -webkit-transform: translateX(80%);
          transform: translateX(80%);
}
.transition-left-leave-to {
  -webkit-transform: translateX(-80%);
          transform: translateX(-80%);
}
.transition-to-right-enter {
  -webkit-transform: translateX(-80%);
          transform: translateX(-80%);
}
.transition-to-right-leave-to {
  -webkit-transform: translateX(80%);
          transform: translateX(80%);
}
.transition-opacity-enter, .transition-opacity-leave-to {
  -webkit-transform: scale(0.8);
          transform: scale(0.8);
  opacity: 0;
}
.transition-opacity-leave, .transition-opacity-enter-to {
  -webkit-transform: scale(1);
          transform: scale(1);
  opacity: 1;
}
.transition-opacity-enter-active {
  transition: 1.4s cubic-bezier(0.19, 1, 0.22, 1);
}
.transition-opacity-leave-active {
  transition: 0.7s cubic-bezier(0.19, 1, 0.22, 1);
}

</style>
