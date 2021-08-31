<template>
    <div class="wrapper">
        <img class="wrapper__img" src="http://www.dell-lee.com/imgs/vue3/user.png" alt="">
        <div class="wrapper__input">
            <input class="wrapper__input__content" type="text" placeholder="请输入手机号">
        </div>
        <div class="wrapper__input">
            <input 
            type="password"
            class="wrapper__input__content"  
            placeholder="请输入密码">
        </div>
         <div class="wrapper__input">
            <input 
            type="password"
            class="wrapper__input__content" 
            placeholder="确认密码">
        </div>
        <div class="wrapper__register-button" @click="handleRegister">注册</div>
        <div class="wrapper__register-link" @click="handleLoginClick">已有帐号去登录</div>
    </div>
</template>

<script>
import {useRouter} from 'vue-router'
export default {
    name: 'Register',
    setup(){
        const router=useRouter();
        const handleRegister=()=>{
            
        }
        const handleLoginClick=()=>{
            router.push({name:"Login"})
        }
        return {handleRegister,handleLoginClick}
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
    &__register-button{
        line-height: .48rem;
        margin: .32rem .4rem .16rem .4rem ;
        background: #0091ff;
        box-shadow: 0 .04rem .08rem rgba(0,145,255,0.32);
        border-radius: .04rem;
        color: #fff;
        font-size: .16rem;
        text-align: center;
    }
    &__register-link{
        text-align: center;
        font-size: .14rem;
        color: $content-notice-fontcolor;
    }
}
</style>