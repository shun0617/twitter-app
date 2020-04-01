<template>
    <div>
        <HeaderAuth />
        <Card :value="text" />
    </div>
</template>

<script>
import HeaderAuth from "../components/HeaderAuth";
import Card from "../components/Card";
export default {
    data() {
        return {
            text: "ログイン"
        };
    },
    components: {
        HeaderAuth,
        Card
    }
};
</script>

<style scoped>

.right {
    align-items: center;
}
.right p {
    margin-right: 20px;
    cursor: pointer;
}
.header {
    margin: 20px;
}
.logo {
    width: 150px;
    cursor: pointer;
}
.flex {
    display: flex;
    justify-content: space-between;
}
button {
    width: 100px;
    text-align: center;
    padding: 8px 0 10px;
    color: #fff;
    background-color: #5419da;
    border-radius: 25px;
    cursor: pointer;
}
.card {
    margin: 100px auto;
    width: 350px;
    background: #fff;
    border-radius: 5px;
    padding: 20px;
}
.card p {
    color: black;
    font-weight: bold;
    text-align: center;
}
input {
    margin-top: 15px;
    width: 80%;
    border-radius: 10px;
    padding: 10px;
    border: 1px solid black;
    color: black;
}
.form {
    text-align: center;
}
@media screen and (max-width: 480px) {
    .logo {
        width: 100px;
        height: 25px;
    }
    .right p {
        margin-right: 10px;
        font-size: 10px;
    }
    .card {
        margin: 100px 20px;
        width: 80%;
    }
}
</style>
