<template>
    <div class="wrapper">
        <img class="wrapper__img" src="http://www.dell-lee.com/imgs/vue3/user.png" alt="">
        <div class="wrapper__input">
            <input 
            class="wrapper__input__content" 
            type="text" 
            placeholder="请输入用户名"
            v-model="data.username">
        </div>
        <div class="wrapper__input">
            <input 
            type="password"
            class="wrapper__input__content"  
            placeholder="请输入密码"
            v-model="data.password">
        </div>
        <div class="wrapper__login-button" @click="handleLogin">登录</div>
        <div class="wrapper__login-link" @click="handleRegisterClick">立即注册</div>
        
    </div>
</template>

<script>
import { useRouter} from 'vue-router'
import { post } from '../../utils/request'
import {reactive} from 'vue'

export default {
    name: 'Login',
    setup(){
        const data=reactive({
            username:'',
            password:''
        })
        const router =useRouter();
        const handleLogin = async() => {
            try{
                const result=await post('/api/user/login',{
                username:data.username,
                password:data.password
            })
            if(result?.errno===0){
                localStorage.isLogin=true;
                router.push({name: 'Home'})
            }else{
                alert('登录失败');
            } 
            }catch(e){
                alert('请求失败')
            } 
        }
        const handleRegisterClick=()=>{
            router.push({name:'Register'})
        }
        return {handleLogin,handleRegisterClick,data}
    }
}
</script>

<style lang="scss" scoped>
@import '../../style/viriables.scss';
.wrapper{
    position: absolute;
    top: 50%;
    left: 0;
    right: 0;
    transform: translateY(-50%);
    &__img{
        display: block;
        margin: 0 auto .4rem;
        width: .66rem;
        height: .66rem;
    }
    &__input{
        height: .48rem;
        margin: 0 .4rem .16rem .4rem;
        padding: 0 .16rem;
        background: #f9f9f9;
        border: 1px solid rgba(0, 0, 0, 0.10);
        border-radius: .06rem;
        &__content{
            line-height: .48rem;
            width: 100%;
            border: none;
            outline: none;
            background: none;
            font-size: .16rem;
            color: $content-notice-fontcolor;
            &::placeholder{
                color: $content-notice-fontcolor;
                letter-spacing: 0;
                line-height: .24rem;
            }
        }
    }
    &__login-button{
        line-height: .48rem;
        margin: .32rem .4rem .16rem .4rem ;
        background: #0091ff;
        box-shadow: 0 .04rem .08rem rgba(0,145,255,0.32);
        border-radius: .04rem;
        color: #fff;
        font-size: .16rem;
        text-align: center;
    }
    &__login-link{
        text-align: center;
        font-size: .14rem;
        color: $content-notice-fontcolor;
    }
}
</style>