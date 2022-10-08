<template>
    <div class="container">
        <nav>
            <ul>
                <li>
                    <nuxt-link to="">
                        <span></span>
                        <span></span>
                        <span></span>
                        <span></span>
                        <img src="@/assets/images/excel.png" alt="">
                        Para Excel
                    </nuxt-link>
                </li>
                <li>
                    <nuxt-link :to="redirect">
                        <span></span>
                        <span></span>
                        <span></span>
                        <span></span>
                        Adicionar
                    </nuxt-link>
                </li>
            </ul>
        </nav>
    </div>
</template>

<script>
export default {
    emits: ['switch-value'],
    props: {
        redirect: String
    }
}
</script>

<style scoped>
.container {
    /* max-width: 1000px; */
    width: 90%;
    margin: 0 auto;
    margin-top: 4.5rem;
}

ul {
    text-align: right;
}

ul li {
    display: inline-block;
    margin-left: 30px;
}

a {
    position: relative;
    display: inline-block;
    padding: 10px 30px;
    height: 40px;
    text-transform: uppercase;
    color: rgba(0, 0, 0, .4);
    background: #fff;
    letter-spacing: 2px;
    font-size: 12px;
    transition: .5s;
}

a:hover {
    color: rgba(0, 0, 0, 1);
    text-decoration: none;
    box-shadow: 3px 3px 20px rgba(0, 0, 0, .14);
}

a span {
    display: block;
    position: absolute;
    background: #2894ff;
}

ul {
    display: flex;
    align-items: center;
    justify-content: flex-end;
}

li:nth-child(1) a span{
    background: #008000;
}

li a{
    display: flex;
    align-items: center;
    justify-content: center;
}

li img {
    width: 20px;
    height: 20px;
    margin-right: 10px;
}

a span:nth-child(1) {
    left: 0;
    bottom: 0;
    width: 1px;
    height: 100%;
    transform: scaleY(0);
    transform-origin: top;
    transition: transform .5s;
}

a:hover span:nth-child(1) {
    transform: scaleY(1);
    transform-origin: bottom;
    transition: transform .5s;
}

a span:nth-child(2) {
    left: 0;
    bottom: 0;
    width: 100%;
    height: 1px;
    transform: scaleX(0);
    transform-origin: right;
    transition: transform .5s;
}

a:hover span:nth-child(2) {
    transform: scaleY(1);
    transform-origin: left;
    transition: transform .5s;
}

a span:nth-child(3) {
    right: 0;
    bottom: 0;
    width: 1px;
    height: 100%;
    transform: scaleY(0);
    transform-origin: top;
    transition: transform .5s;
}

a:hover span:nth-child(3) {
    transform: scaleY(1);
    transform-origin: bottom;
    transition: transform .5s;
}

a span:nth-child(4) {
    left: 0;
    top: 0;
    width: 100%;
    height: 1px;
    transform: scaleX(0);
    transform-origin: right;
    transition: transform .5s;
}

a:hover span:nth-child(4) {
    transform: scaleY(1);
    transform-origin: left;
    transition: transform .5s;
}


@media (max-width: 700px) {
    li {
        display: block;
        width: 100%;
        margin-bottom: 1rem;
    }
}

</style>