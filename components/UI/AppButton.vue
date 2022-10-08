<template>
    <div class="btn">
        <button>
            <span></span>
            <span></span>
            <span></span>
            <span></span>
            Adicionar
        </button>
    </div>
</template>

<style scoped>
.btn {
    width: 100%;
    text-align: center;
    margin-top: 3rem;
}

button {
    cursor: pointer;
    position: relative;
    display: inline-block;
    padding: 10px 28px;
    text-transform: uppercase;
    color: rgba(255, 255, 255, .4);
    border: none;
    outline: none;
    background: #262c37;
    letter-spacing: 2px;
    font-size: 12px;
    transition: .5s;
}

button:hover {
    color: rgba(255, 255, 255, .8);
    text-decoration: none;
}

button span {
    display: block;
    position: absolute;
    background: goldenrod;
}

button span:nth-child(1) {
    left: 0;
    bottom: 0;
    width: 1px;
    height: 100%;
    transform: scaleY(0);
    transform-origin: top;
    transition: transform .5s;
}

button:hover span:nth-child(1) {
    transform: scaleY(1);
    transform-origin: bottom;
    transition: transform .5s;
}

button span:nth-child(2) {
    left: 0;
    bottom: 0;
    width: 100%;
    height: 1px;
    transform: scaleX(0);
    transform-origin: right;
    transition: transform .5s;
}

button:hover span:nth-child(2) {
    transform: scaleY(1);
    transform-origin: left;
    transition: transform .5s;
}

button span:nth-child(3) {
    right: 0;
    bottom: 0;
    width: 1px;
    height: 100%;
    transform: scaleY(0);
    transform-origin: top;
    transition: transform .5s;
}

button:hover span:nth-child(3) {
    transform: scaleY(1);
    transform-origin: bottom;
    transition: transform .5s;
}

button span:nth-child(4) {
    left: 0;
    top: 0;
    width: 100%;
    height: 1px;
    transform: scaleX(0);
    transform-origin: right;
    transition: transform .5s;
}

button:hover span:nth-child(4) {
    transform: scaleY(1);
    transform-origin: left;
    transition: transform .5s;
}

</style>