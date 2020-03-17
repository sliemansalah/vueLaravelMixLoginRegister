<template>
  <div class="m-grid m-grid--hor m-grid--root m-page">
			<div class="m-grid__item m-grid__item--fluid m-grid m-grid--hor m-login m-login--signin m-login--2 m-login-2--skin-2" id="m_login" style="background-image: url(../../../assets/app/media/img//bg/bg-3.jpg);">
				<div class="m-grid__item m-grid__item--fluid	m-login__wrapper">
					<div class="m-login__container">
						<div v-if="signIn" class="m-login__signin">
							<div class="m-login__head">
								<h3 class="m-login__title">Sign In</h3>
							</div>
							<form class="m-login__form m-form" action="">
								<div class="form-group m-form__group">
									<input v-model="user.email" class="form-control m-input" type="text" placeholder="Email" name="email" autocomplete="off">
								</div>
								<div class="form-group m-form__group">
									<input v-model="user.password" class="form-control m-input m-login__form-input--last" type="password" placeholder="Password" name="password">
								</div>
								<div class="m-login__form-action"> 
									<a @click="login" id="m_login_signin_submit" class="btn btn-focus m-btn m-btn--pill m-btn--custom m-btn--air m-login__btn m-login__btn--primary">Sign In</a>
								</div>
							</form>
						</div>
                        	<div v-else class="m-login__signin">
							<div class="m-login__head">
								<h3 class="m-login__title">Sign UP</h3>
							</div>
							<form class="m-login__form m-form" action="">
								<div class="form-group m-form__group">
									<input v-model="user.email" class="form-control m-input" type="text" placeholder="Email" name="email" autocomplete="off">
								</div>
								<div class="form-group m-form__group">
									<input v-model="user.password" class="form-control m-input m-login__form-input--last" type="password" placeholder="Password" name="password">
								</div>
								<div class="m-login__form-action"> 
									<a @click="register" id="m_login_signin_submit" class="btn btn-focus m-btn m-btn--pill m-btn--custom m-btn--air m-login__btn m-login__btn--primary">Register</a>
								</div>
							</form>
						</div>
					
                    <div v-if="signIn" class="m-login__account">
							<span class="m-login__account-msg">
								Don't have an account yet ?
							</span>&nbsp;&nbsp;
							<span @click="signIn=!signIn" id="m_login_signup" class="m-link m-link--light m-login__account-link">Sign Up</span>
                        </div>

                            <div v-else class="m-login__account">
							<span class="m-login__account-msg">
								You are have an account
							</span>&nbsp;&nbsp;
							<span @click="signIn=!signIn" id="m_login_signup" class="m-link m-link--light m-login__account-link">Sign In</span>
                        </div>
					</div>
				</div>
			</div>
		</div>

</template>

<script>
import axios from 'axios'
export default {
    data(){
        return {
            signIn:true,
            user:{
                email:'',
                password:'',
            },
        }
    },
    methods:{
        login(){
            axios.post('https://reqres.in/api/login',this.user).then(res=>{
              if(res.data.token) {
                  localStorage.setItem('user',this.user.email);
                  this.$router.go(0)
              }
            }).catch(err=>{
                console.log('error',err)
            })
        }
	},
}
</script>

<style scoped>
a{
    color: #fff !important;
}
#m_login_signup:hover{
    cursor: pointer;
}
</style>