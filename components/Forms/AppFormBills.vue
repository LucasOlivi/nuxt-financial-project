<template>
    <div class="container">
        <div class="rows-container">
            <form @submit.prevent="submit" ref="submitNewIncoming">
                <div class="rows">
                    <div class="row">
                        <div class="inputBox">
                            <the-mask
                            :mask="['##/##/####']"
                            masked="false"
                            required
                            v-model="body.date"
                            />
                            <span>Data</span>
                        </div>
                    </div>
                    <div class="row">
                        <div class="inputBox">
                            <money 
                            v-bind="money"
                            v-model="body.value"
                            required
                            />
                            <span>Valor</span>
                        </div>
                    </div>
                    <div class="row type">
                        <p>Tipo</p>
                        <div class="radio">
                            <label> 
                                <input 
                                type="radio" 
                                name="despesa" 
                                value="Pessoal"
                                v-model="checkBoxValue"
                                required> Pessoal </label>
                            <label> 
                                <input 
                                type="radio" 
                                name="despesa" 
                                value="Empresa"
                                v-model="checkBoxValue"
                                required> Empresa </label>        
                        </div>
                    </div>
                    <div class="row" v-show="checkBoxValue" >
                        <select v-model="body.account" required>
                            <option selected value="">Escolha uma Conta</option>

                            <!-- Personal -->
                            <option 
                            v-show="checkBoxValue == 'Pessoal'"
                            v-for="list in listPerson"
                            :value="list"
                            >{{list}}</option>

                            <!-- Empresa -->
                            <option
                            v-show="checkBoxValue == 'Empresa'"
                            v-for="list in listCompany"
                            :value="list"
                            >{{list}}</option>
                        </select>
                        <p 
                        class="selected-account" 
                        v-show="body.account" >
                            Conta Selecionada:
                            <em>{{body.account}}</em></p>
                    </div>
                </div>
                <div class="rows-obs">
                    <div class="row">
                        <div class="inputBox">
                            <textarea v-model="body.obs" type="text" class="obs" placeholder="Observações"></textarea>
                        </div>
                    </div>
                    <AppButton/>
                </div>
                <AppIcon
                redirect="/administrator/bill"
                />
            </form>
            <AppTableNewIncoming
            :incomings="bodyList"
            />
        </div>
        <notifications 
        group="foo" 
        position="top right"
        animation-type="velocity" 
        :animation="animation"
        />
    </div>
</template>

<script>
import AppIcon from '~/components/UI/AppIcon.vue'
import AppButton from '@/components/UI/AppButton.vue'
import AppTableNewIncoming from '@/components/Tables/AppTableNewIncoming.vue'

export default {
    data() {
        return {
            body: {
                date: '',
                value: '',
                account: '',
                obs: ''
            },
            money: {
                decimal: ',',
                thousands: '.',
                prefix: 'R$ ',
                suffix: '',
                precision: 2,
                masked: false
            },
            bodyList: [],
            listPerson: ['Aluguel', 'Energia Elétrica', 'Água', 'Internet', 'Correios'],
            listCompany: ['Publicidade', 'Brindes', 'Juros Passivos', 'Despesas Bancárias'],
            checkBoxValue: ''
        }
    },
    methods: {
        submit() {
            this.$refs.submitNewIncoming.reset()
            this.bodyList.push({
                date: this.body.date,
                account: this.body.account,
                value: this.body.value
            })
            // body for submit

            let body = {
                date: this.body.date,
                value: this.body.value,
                type: this.checkBoxValue,
                account: this.body.account,
                obs: this.body.obs
            }

            // console.log(body, 'body')

            // body for submit
            this.notification()
        },
        checkBox() {

        },
        notification() { //Axios Interceptores
            this.$notify({
                group: 'foo',
                title: 'Important message',
                text: 'Valor adicionado com sucesso!',
                type: 'success'
            });
        }
    },
    computed: {
        animation () {
            return {
            /**
             * Animation function
             * 
             * Runs before animating, so you can take the initial height, width, color, etc
             * @param  {HTMLElement}  element  The notification element
             */
            enter (element) {
                let height = element.clientHeight
                return {
                // animates from 0px to "height"
                height: [height, 0],

                // animates from 0 to random opacity (in range between 0.5 and 1)
                opacity: [Math.random() * 0.5 + 0.5, 0]
                }
            },
            leave: {
                height: 0,
                opacity: 0
            }
            }
        }
    },
    components: {
        AppIcon,
        AppButton,
        AppTableNewIncoming
    },
}
</script>

<style scoped>
.container {
    position: relative;
}

.rows-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
}

.rows, .rows-obs {
    position: relative;
    background: #fff;
    border-radius: 8px;
    box-shadow: 3px 3px 10px rgba(0, 0, 0, .1);
    width: 100%;
    margin: 0 auto;
    padding: 20px;
}

.rows-obs {
    margin-top: 4.3rem;
}

.inputBox {
    position: relative;
    width: 100%;
    margin-bottom: 30px;
}

.inputBox input, textarea{
    width: 100%;
    padding: 10px;
    border: 1px solid rgba(0, 0, 0, .25);
    border-radius: 5px;
    outline: none;
    color: black;
    font-size: .9em;
    transition: .5s;
}

textarea {
    resize: none;
}

select {
    border: none;
    border-bottom: 1px solid rgba(0, 0, 0, .2);
    border-top: 1px solid rgba(0, 0, 0, .2);
    border-right: 10px solid white;
    width: 100%;
    padding: 10px;
    border-radius: 5px;
    outline: none;
    color: black;
    font-size: .9em;
}

.selected-account {
    color: grey;
    font-size: .9em;
    margin-top: .5rem;
}

.selected-account em {
    font-weight: 500;
}

.obs {
    background-color: white;
    height: 100px;
}

.inputBox span {
    position: absolute;
        left: 0;
    padding: 10px;
    pointer-events: none;
    font-size: 1em;
    color: rgba(0, 0, 0, .3);
    text-transform: uppercase;
    transition: .5s;
}

::placeholder {
    font-size: 1em;
    color: rgba(0, 0, 0, .3);
    text-transform: uppercase;
}

.inputBox input:valid ~ span,
.inputBox input:focus ~ span {
    color: goldenrod;
    transform: translateX(10px) translateY(-7px);
    font-size: .65em;
    padding: 0 10px;
    background: #fff;
    border: none;
    border-left: 1px solid rgba(0, 0, 0, .25);
    border-right: 1px solid #000;
    letter-spacing: .2em;
}

.inputBox input:valid,
.inputBox input:focus{
    border: 1px solid rgba(0, 0, 0, .5);
}

/*Radio*/
.type {
    border: none;
    border-bottom: 1px solid rgba(0, 0, 0, .2);
    border-top: 1px solid rgba(0, 0, 0, .2);
    border-right: 10px solid white;
    margin-bottom: 20px;
    padding: 6px 0;
}

.type p {
    font-size: 1em;
    color: rgba(0, 0, 0, .7);
    text-transform: uppercase;
    margin-left: 12px;
}

.radio {
    padding-top: 3%;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    height: 48px;
    border-radius: 4px;
}

input[type="checkbox"], input[type="radio"] {
    position: relative;
        top: 0;
    width: 20px;
    height: 20px;
    margin-left: 18px;
    -webkit-appearance: none;
    outline: none;
    transition: .5s;
}

input[type="checkbox"]::before, input[type="radio"]::before {
    content: '';
    position: absolute;
        top: 0;
        left: 0;
    width: 100%;
    height: 100%;
    border: 3px solid #777;
    transition: .3s ease;
}

label {
    font-size: 1rem;
}

input:checked[type="checkbox"]::before,input:checked[type="radio"]::before {
    border-top: none;
    border-left: none;
    width: 10px;
    border-color: rgb(7, 202, 7);
    transform: rotate(45deg);
}
</style>