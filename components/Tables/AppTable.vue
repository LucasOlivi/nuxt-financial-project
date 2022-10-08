<template>
    <div class="container">
        <table>
            <thead>
            <tr>
                <th>Data</th>
                <th>Conta</th>
                <th>Observações</th>
                <th v-show="isShown == 'true'" >Tipo</th>
                <th>Valor</th>
            </tr>
            </thead>
            <tbody>
              <tr v-for="item in body" >
                <td>{{item.date}}</td>
                <td>{{item.account}}</td>
                <td :title="item.obs">{{item.obs | truncate(70)}}</td>
                <td v-show="isShown == 'true'" >{{item.type}}</td>
                <td>{{item.value | currency('R$ ', 2)}}</td>
              </tr>
            </tbody>
            <tfoot>
              <tr v-if="isShown == 'false'" >
                  <td colspan="3" align="right">Total</td>
                  <td>{{totalValue | currency('R$ ', 2)}}</td>
              </tr>
              <tr v-else >
                  <td colspan="4" align="right">Total</td>
                  <td>{{totalValue | currency('R$ ', 2)}}</td>
              </tr>
            </tfoot>
      </table>
    </div>
</template>

<script>

export default {
  data() {
    return {
      body: [
        {
          date: '20/08/2022',
          account: 'account',
          obs: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Similique natus ipsa delectus dolores nostrum aliquam vel incidunt illum consectetur architecto earum, perspiciatis unde voluptatum, facere cumque sapiente beatae obcaecati maxime?',
          type: 'Empresa',
          value: 80000
        },
        {
          date: '21/08/2022',
          account: 'account',
          obs: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Similique natus ipsa delectus dolores nostrum aliquam vel incidunt illum consectetur architecto earum, perspiciatis unde voluptatum, facere cumque sapiente beatae obcaecati maxime?',
          type: 'Pessoal',
          value: 100000
        },
        {
          date: '22/08/2022',
          account: 'account',
          obs: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Similique natus ipsa delectus dolores nostrum aliquam vel incidunt illum consectetur architecto earum, perspiciatis unde voluptatum, facere cumque sapiente beatae obcaecati maxime?',
          type: 'Empresa',
          value: 70000
        },
      ]
    }
  },
  props: {
    isShown: String
  },
  computed: {
      totalValue() {
          const array = this.body
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

.container {
    margin-top: .8rem;
}

table {
  border-collapse: collapse;
  box-shadow: 0 5px 10px #e1e5ee;
  background-color: white;
  text-align: left;
  overflow: hidden;
  margin: 0 auto;
  border-radius: 4px;
  width: 90%;
}

td {
  padding: 1rem 2rem;
}

a {
  text-decoration: none;
  color: #2962ff;
}

thead {
  box-shadow: 0px 5px 10px #e1e5ee;
}

tbody tr, thead tr {
  text-align: center;
}

tbody tr td:last-child,
tfoot tr {
  white-space: nowrap;
}

th {
  padding: 1rem 2rem;
  text-transform: uppercase;
  letter-spacing: 0.1rem;
  font-size: 0.7rem;
  font-weight: 900;
}

.status {
  border-radius: .2rem;
  padding: 0.2rem 1rem;
  text-align: center;
}

.amount {
  text-align: right;
}

.status .status-pending {
  background-color: #fff0c2;
  color: #a68b00;
}

.status .status-paid {
  background-color: #c8e6c9;
  color: #388e3c;
}

.status .status-unpaid {
  background-color: #ffcdd2;;
  color: #c62828;
}

tr:nth-child(even) {
  background-color: #f4f6fb;;
}

tfoot tr {
    border-top: 1px dashed rgba(0, 0, 0, .4);
    text-align: center;
}

tfoot tr td:last-child {
  font-weight: 600;
  letter-spacing: .8px;
}

</style>