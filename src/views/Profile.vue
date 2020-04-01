<template>
    <div class="flex" v-if="hoge">
        <div class="left">
            <SideNavi />
        </div>
        <div class="right">
            <div class="title">
                <p>プロフィール</p>
            </div>
            <div class="profile">
                <div class="flex-profile">
                    <p class="profile-name">{{name}}</p>
                    <div @click="edit">
                        <button>変更する</button>
                    </div>
                </div>
                <p class="text" v-if="active">{{profile}}</p>
                <input type="text" v-model="profile" v-else />
            </div>
            <Message />
        </div>
    </div>
    <div v-else>
        <Header />
        <div class="profile">
            <div class="flex-profile">
                <p class="profile-name">{{name}}</p>
                <div @click="edit">
                    <button>変更する</button>
                </div>
            </div>
            <p class="text" v-if="active">{{profile}}</p>
            <input type="text" v-model="profile" v-else />
        </div>
        <Message />
        <Footer />
    </div>
</template>
<script>
    import axios from "axios";
    import Header from "../components/Header";
    import Footer from "../components/Footer";
    import SideNavi from "../components/SideNavi";
    import Message from "../components/Message";
    export default {
        data() {
            return {
                active: true,
                name: this.$store.state.user.name,
                profile: this.$store.state.user.profile,
                hoge: ""
            };
        },
        methods: {
            edit() {
                if(!this.active) {
                    axios
                    .put("https://cli.vuejs.org/guide/deployment.html/user", {
                        email: this.$store.state.user.email,
                        profile: this.profile
                    })
                    .then(response => {
                        this.$store.dispatch("changeUserData", {
                            profile: this.profile
                        });
                        console.log(response);
                    });
                }
                this.active = !this.active;
            }
        },
        created() {
            if(screen.width >= 480) {
                this.hoge = true;
            } else {
                this.hoge = false;
            }
        },
        components: {
            SideNavi,
            Header,
            Footer,
            Message
        }
    };
</script>
<style scoped>
.left {
    width: 22%;
    height: 100vh;
    border-right: 1px solid white;
}
.right {
    width: 78%;
    height: 100vh;
}
.flex {
    display: flex;
}
.profile {
    padding: 20px;
    border-bottom: 1px solid white;
}
.profile-name {
    font-size: 24px;
}
.title {
    border-bottom: 1px solid white;
}
.title p {
    font-size: 20px;
    font-weight: bold;
    margin: 15px;
}
.flex-profile {
    display: flex;
    justify-content: space-between;
}
@media screen and (max-width: 480) {
    .text {
        font-size: 10px;
    }
}
</style>