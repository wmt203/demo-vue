<template>
    <div>
        <form action="" v-if="!isReg">
            用户名
            <input type="text" v-model="name">
            密码
            <input type="password" v-model="password">
            <button type="button" @click="login()">登录</button>
            <button type="button" @click="reg()">注册</button>
        </form>
        <form action="" v-else>
            用户名
            <input type="text" v-model="name">
            密码
            <input type="password" v-model="password">
            重复密码
            <input type="password" v-model="repeat">
            <button type="button" @click="addUser()">确定</button>
            <button type="button" @click="cancel()">取消</button>
        </form>
    </div>
</template>

<script>
    export default {
        name: "Login",
        data(){
            return{
                name:'',
                password:'',
                repeat:'',
                isReg:false
            }
        },
        methods:{
            login(){
                if(localStorage.getItem('name') === this.name && localStorage.getItem('password') === this.password){
                    this.name = ''
                    this.password =''
                    this.$router.push('/home/list')
                }else{
                    alert('用户名密码不正常')
                }
            },
            reg(){
                this.isReg = true
            },
            addUser(){
                if(this.password === this.repeat){
                    localStorage.setItem('name',this.name)
                    localStorage.setItem('password',this.password)
                    this.name = ''
                    this.password =''
                    this.repeat = ''
                    this.reg = false
                }else{
                    alert('密码不一致')
                }

            },
            cancel(){
                this.isReg = false
            }
        }
    }
</script>

<style scoped>

</style>