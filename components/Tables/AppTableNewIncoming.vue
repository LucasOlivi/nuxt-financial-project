<template>
    <div class="container">
        <div class="header-fixed">
            <table class="invoice-table">
                <thead>
                    <tr>
                        <td>CONTA</td>
                        <td>DATA</td>
                        <td>VALOR</td>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="incoming in incomings">
                        <td>{{incoming.account}}</td>
                        <td class="unit" >{{incoming.date}}</td>
                        <td>{{incoming.value | currency('R$ ', 2)}}</td>
                    </tr>
                    
                </tbody>
                <tfoot>
                    <tr>
                        <td colspan="2" align="right">Total</td>
                        <td>{{totalValue | currency('R$ ', 2)}}</td>
                    </tr>
                </tfoot>
            </table>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            incomings: {
                type: Array,
                required: true
            }
        },
        computed: {
            totalValue() {
                const array = this.incomings
                let sum = 0
                for(let i = 0; i < array.length; i++) {
                    sum = sum + array[i].value
                }
                return sum
            }
        }
    }
</script>

<style scoped>

::-webkit-scrollbar {
    width: 10px;
    height: 5px;
}
::-webkit-scrollbar-thumb {
    background-color: #fff;
    border: 1px solid rgba(0, 0, 0, .075);
    border-radius: 20px;
}
::-webkit-scrollbar-track {
    background-color: rgba(0, 0, 0, .2);
    border-radius: 20px;
    box-shadow: inset 0 0 6px rgba(0, 0, 0, .3);
}

.header-fixed {
    height: 100%;
    max-height: 536px;
    overflow: auto;
    max-width: 25.9em;
    width: 100%;
    border-radius: 6px;
    margin: 0 auto;
}

.invoice-table {
    border-collapse: collapse;
    max-width: 25em;
    width: 100%;
    background: white;
    border-radius: 5px;
    box-shadow: 3px 3px 10px rgba(0, 0, 0, .1);
    margin: 0 auto;
}

.invoice-table thead tr {
    border-bottom: 1px dashed grey;
}
.invoice-table tfoot tr {
    border-top: 1px dashed grey;
}

.invoice-table thead tr td {
    font-size: 16px;
    letter-spacing: 1px;
    color: grey;
    padding: 8px;
}

.invoice-table tfoot tr td {
    font-size: 18px;
    letter-spacing: 1px;
    color: green;
    padding: 8px;
    white-space: nowrap;
}

.invoice-table tbody tr td {
    padding: 12px 8px;
    white-space: nowrap;
    font-size: 16px;
}

.invoice-table tbody tr:hover {
    color: goldenrod;
}

.invoice-table thead tr td:nth-last-child(1),
.invoice-table tbody tr td:nth-last-child(1),
.invoice-table tfoot tr td:nth-last-child(1) {
    text-align: right;
    width: 130px;
}

.invoice-table tbody span {
    font-size: 10px;
    color: grey;
    font-style: italic;
}

@media (max-width: 600px) {
    .invoice-table {
        width: 90%;
    }
}
</style>