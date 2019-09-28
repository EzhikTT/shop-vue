<template>
    <header>
        <div class="logo">SH</div>
        <nav>
            <a>Женщинам</a>
            <a>Мужчинам</a>
            <a>Детям</a>
            <a>Новинки</a>
            <a>О нас</a>
        </nav>
        <div class="user">
            <div v-on:click="togglePopup()">Войти</div>
            <div>Корзина(0)</div>
        </div>
        <div class="popup" v-show="showPopup">
            <div class="body">
                <form>
                    <input type="text"
                           placeholder="login"
                           v-model="login"/>
                    <input type="password"
                           placeholder="password"
                           v-model="password"/>

                    <button>Войти</button>
                </form>
            </div>
        </div>
    </header>
</template>

<script>
    export default {
        name: 'HeaderComponent',
        data(){
            return {
                showPopup: false,
                login: '',
                password: ''
            };
        },
        methods: {
            singIn(){
                fetch(
                    'http://192.168.64.2/api/login.php',
                    {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json'
                        },
                        body: JSON.stringify({
                            login: this.login,
                            password: this.password
                        })
                    }
                ).then(res => res.json).then(res => {


                });
            },
            togglePopup(){
                this.showPopup = !this.showPopup;
            }
        }
    };
</script>

<style scoped>
    header{
        display: flex;
    }
    .logo{
        padding: 20px;
        background-color: #000;
        color: white;
        margin-right: 3rem;
    }
    nav{
        display: flex;
        align-items: center;
    }
    nav a:not(:last-child){
        margin-right: 15px;
    }
    .user{
        margin-left: auto;
        display: flex;
        align-items: center;
    }
    .user div{
        margin-right: 20px;
    }
</style>