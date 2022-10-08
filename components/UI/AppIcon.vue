<template>
    <nuxt-link :to="redirect" class="icon">
    <i class='bx bx-arrow-back'></i>
        <span>Voltar</span>
    </nuxt-link>  
</template>

<script>
    export default {
        props: {
            redirect: String
        }
    }
</script>

<style scoped>
.icon {
    cursor: pointer;
    position: absolute;
        top: -60px;
        left: 0;
    height: 55px;
    width: 55px;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 1px solid rgba(0, 0, 0, .1);
    text-align: center;
    transition: .3s ease;
    z-index: 10000;
}

.icon:hover{
    border-radius: 50%;
    border: 1px solid grey;
}

.icon:hover span {
    display: block;
    opacity: 1;
    transition: .3s ease;
}

.icon span {
    position: absolute;
        top: -35px;
    background: rgba(0, 0, 0, .2);
    color: white;
    font-size: 11px;
    font-weight: 300;
    width: 100%;
    padding: 5px;
    border-radius: 5px;
    transition: .3s ease;
    display: none;
    opacity: 0;
}

.bx-arrow-back {
    font-size: 28px;
}

a {
    text-decoration: none;
    color: black;
}
</style>