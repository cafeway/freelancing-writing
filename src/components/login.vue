 
<template>
<div class="container">
        <div class="card">
            <div class="card__header">
                <h2 class="title">Sign <span>In</span></h2>
            </div>
            <form action="">
                <div class="card__body">
                    <label for="email">Email Address</label>
                    <input type="email" placeholder="ZiyovuddinDEv@gmail.com" required id="email" v-model="form.email">
                    <label for="password">Password</label>
                    <input type="password" placeholder="your password" required  id="password" v-model="form.password">
                </div>
                <div class="card__footer">
                    <button type="button" id="signin" class="btn_sign-in-up" @click="submit()">Sign In</button>
                    <p @click="toRegister()">Don't have an account? <a href="##">Sign Up</a>.</p>
                    <p>Forgot password? <a href="#">Click here</a>.</p>
                </div>
            </form>
        </div>
</div>
</template>

<script>
import firebase from 'firebase'
export default {
  name: 'Login',
  data(router) {
    return {
      form: {
        email: '',
        password: ''
      }
    }
  },
  methods: {
    submit: function () {
      firebase.auth().signInWithEmailAndPassword(this.form.email, this.form.password).then(data => {
        this.$router.push('/')
      })
      .catch(err => {
        this.$swal({
          icon: 'warning',
          text: err.message
        })
      })
    },
    toRegister: function () {
      this.$router.push('/register')
    }
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
}
body {
    width: 100%;
    height: 100%;
    margin: 0;
    padding: 0;
    font-family: 'Quicksand', sans-serif;
}
a {
    text-decoration: none;
    color: #C06C84;
    transition: all 300ms;
}
a:hover {
    opacity: .5;
}
.container {
    font-size: 1rem;
    width: 100%;
    height: 100vh;
    background: linear-gradient(70deg, #8d030f, #da0dad, #6d0522);
    display: flex;
    justify-content: center;
    align-items: center;
    background-image: url('https://images.pexels.com/photos/546819/pexels-photo-546819.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260');
    
}
/* Card */
.card {
    width: 100%;
    max-width: 400px;
    height: auto;
    margin: 0 auto 0 auto;
    padding: 0 1.5rem 2rem;
    color: #fafafa;
    border: 1px solid rgba(255, 255, 255, .5);
    border-radius: 4px;
    /* background-image: url('https://images.pexels.com/photos/356056/pexels-photo-356056.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260'); */
    /* background: linear-gradient(70deg, #0ac1da, #e9dfe7, #17c5b4) ; */
    box-shadow: inset 4px 4px 5px rgba(255,255,255,0.3), 
     inset -4px -4px 5px rgba(0, 0, 0, 0.1), 
     10px 40px 40px rgba(0,0,0,0.1);
    backdrop-filter: blur(50px);
    -webkit-backdrop-filter: blur(50px);
}
/* Header */
.card__header {
    padding-bottom: 1rem;
}
.card__header h2.title {
    text-transform: uppercase;
    text-align: center;
    letter-spacing: .2rem;
}
.card__header h2.title span {
    color: #C06C84;
}
/* Body */
.card__body {
    width: 100%;
    padding-bottom: 1rem;
}
/* Label */
label {
    display: block;
    margin-bottom: .5rem;
    font-size: .75em;
    letter-spacing: .2rem;
    text-transform: uppercase;
}
/* Input */
input {
    display: block;
    margin-bottom: 1.25rem;
    padding-left: .8rem;
    width: 100%;
    height: 2.75rem;
    font-size: 1rem;
    color: rgba(250, 250, 250, .9);
    background-color: rgba(255, 255, 255, 0);
    border: 1px solid rgba(255, 255, 255, 1);
    border-radius: 4px;
    outline: none;
    transition: background-color .5s;
    box-shadow: -10px -10px 10px rgba(255,255,255,0.2),
	            15px 15px 15px rgba(235, 228, 228, 0.1),
	            inset -10px -10px 10px rgba(245, 241, 241, 0.2);
	            /* inset 15px 15px 15px rgba(0, 0, 0, 0.1); */
}
input::placeholder, input::-webkit-input-placeholder  {
    color: rgba(255, 255, 255, .5);
    
}
input:hover,
input:focus {
    background-color: rgba(255, 255, 255, .5);
    
}
/* Footer */
.card__footer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
/* Button */
.btn_sign-in-up {
    cursor: pointer;
    font-size: 1rem;
    font-weight: bold;
    text-transform: uppercase;
    color: rgba(0, 0, 0, .5);
    padding: 1rem 2rem;
    border: 1px solid transparent;
    border-radius: 2rem;
    outline: none;
    background-color: rgba(255, 255, 255, .8);
    transition: all .5s;
    box-shadow: inset 4px 4px 5px rgba(255,255,255,0.3),
    inset -4px -4px 5px rgba(0, 0, 0, 0.1),
    10px 40px 40px rgba(0,0,0,0.1);
}
.btn_sign-in-up:hover {
    background-color: rgba(255, 255, 255, .2);
    border: 1px solid rgba(255, 255, 255, 1);
    color: rgb(255, 255, 255);
}
.card__footer p {
    margin-bottom: 0;
    font-size: .8rem;
}
/* Responsive */
@media (max-width: 530px) {
    .card {
        margin-left: 2rem;
        margin-right: 2rem;
    }
}
</style>
