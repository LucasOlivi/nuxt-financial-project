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
                    <div class="row">
                        <select v-model="body.account">
                            <option selected value="">Escolha uma Conta</option>
                            <option value="Receita de Venda">Receita de Venda</option>
                            <option value="Receita de Clientes">Receita de Clientes</option>
                            <option value="Receita de Comissionados">Receita de Comissionados</option>
                            <option value="Outras Receitas">Outras Receitas</option>
                        </select>
                    </div>
                </div>
                <div class="rows-obs">
                    <div class="row">
                        <div class="inputBox">
                            <textarea v-model="body.obs" type="text" class="obs" placeholder="Observações"></textarea>
                            <!-- <span>Observações</span> -->
                        </div>
                    </div>
                    <AppButton/>
                </div>
                <AppIcon
                redirect="/administrator/incoming"
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
            bodyList: []
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
            this.notification()
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
</style>