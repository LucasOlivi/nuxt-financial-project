<template>
    <div class="container">
        <div class="rows">
            <div class="row">
                <div class="icon">
                    <i class='bx bx-brightness'></i>
                </div>
                <div class="content">
                    <h4>The Title of the KPI</h4>
                    <p>80</p>
                </div>
            </div>
            <div class="row">
                <div class="icon">
                    <i class='bx bx-brightness'></i>
                </div>
                <div class="content">
                    <h4>The Title of the KPI</h4>
                    <p>80</p>
                </div>
            </div>
            <div class="row">
                <div class="icon">
                    <i class='bx bx-brightness'></i>
                </div>
                <div class="content">
                    <h4>The Title of the KPI</h4>
                    <p>80</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    components: {},
}
</script>

<style scoped>
.rows {
    width: 90%;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-column-gap: 20px;
    margin: 0 auto;
}

.row {
    padding: 38px 15px;
    border-radius: 0px;
    transition: .4s ease;
    background: white;
    border-radius: 4px;
    display: grid;
    grid-template-columns: 25% 75%;
    grid-column-gap: 20px;
}

.row:hover {
    border-radius: 12px;
    transform: scale(1.03);
    box-shadow: 3px 3px 10px rgba(0, 0, 0, .1);
}

.row .icon {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
}
.row .icon:before {
    content: '';
    position: absolute;
        right: 0;
        top: 50%;
    transform: translateY(-50%);
    width: 1px;
    height: 80%;
    background: grey;
}

.icon i {
    font-size: 28px;
}

/* .content h4 {
    font-weight: 300;
    font-size: .9rem;
    color: goldenrod;
    text-transform: uppercase;
}

.content p {

} */

</style>
