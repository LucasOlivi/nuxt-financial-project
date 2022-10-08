<template>
    <h2
    :class="titleStyle"
    >{{titleText}}</h2>
</template>

<script>
export default {
    props: {
        titleText: String,
        titleStyle: String
    }
}
</script>

<style scoped>
h2 {
    position: relative;
    width: 100%;
    text-align: center;
    margin-bottom: 3.5rem;
}

.style-1 {
    position: relative;
    width: 100%;
    text-align: center;
}

.style-1::before {
    content: '';
    position: absolute;
        bottom: -13px;
        left: 50%;
    transform: translateX(-50%);
    width: 100px;
    height: 4px;
    border-radius: 8px;
    background: #11101d;
}
</style>