<template>
    <Nav :login="login" />
    <section class="login flex flex_ai_c flex_jc_c">
        <div class="login_signup" v-if="page">
            <h2>Sign Up</h2>
            <p>Sign up with an account, and travel the world!</p>
            <form>
                <input type="text" name="name" placeholder="Name" required><br>
                <input type="text" name="email" placeholder="Email" required><br>
                <input type="password" name="password" placeholder="Password" required><br>
                <button class="submit">Submit</button>
            </form>
            <p class="login_info">Already a member? <span @click="switchPage" class="info">Login!</span></p>
        </div>
        <div class="login_signup" v-if="page === false">
            <h2>Login</h2>
            <p>Log into your account, and travel the world!</p>
            <form>
                <input type="text" name="email" placeholder="Email" required><br>
                <input type="password" name="password" placeholder="Password" required><br>
                <button class="submit">Submit</button>
            </form>
            <p class="login_info">Not a member? <span @click="switchPage" class="info">Sign Up!</span></p>
        </div>
        <div class="login_signup" v-if="msg">
            <h2>Password Retrieval</h2>
            <p>Log into your account, and travel the world!</p>
            <form>
                <input type="text" name="email" placeholder="Email" required><br>
                <button class="submit">Submit</button>
            </form>
            <p class="login_info">Back to <span @click="switchPage" class="info">Login!</span></p>
        </div>
    </section>
    <Footer />
</template>

<script>
    import Nav from "@/components/Nav"
    import Footer from "@/components/Footer"
    import { onMounted, ref } from 'vue'

    export default {
        name: 'Login',
        props: ['msg'],
        components: {Nav,Footer},
        setup(props,context){
            
            const login = ref(true)
            const page = ref(null)
            const msg = ref(false)

            const a = onMounted(()=>{
                // console.log(props.msg == 'hello')
                if(props.msg === undefined){
                    page.value = false
                }else if(props.msg == 'hello'){
                    msg.value = true
                }
            })

            document.body.scrollTop

            document.body.addEventListener('scroll', function (ev) {
                if(document.body.scrollTop >= 10){
                    //scrolls down
                    login.value = false
                }else if(document.body.scrollTop <= 10){
                    //scrolls up
                    login.value = true
                }
            }, true)

            const switchPage = ()=>{
                page.value = !page.value
                msg.value = false
            }

            return{login,page,switchPage,msg}
        }
    }
</script>