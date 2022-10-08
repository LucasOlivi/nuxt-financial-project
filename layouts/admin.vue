<template>
    <div>
      <div 
          class="sidebar"
          :class="{active: isActive}"
          >
            <div class="logo_content">
                <h3 class="logo_text">W3 Tech</h3>
                <i 
                @click="switchValue"
                class='bx bx-menu'></i>
            </div>
            <div class="pages_title" :class="{active: isActive}">
                <h3>Páginas</h3>
            </div>
            <ul :class="{active: isActive}">
                <li>
                    <i class='bx bxs-dashboard'></i>
                    <p>Dashboard</p>
                    <nuxt-link to="/administrator"></nuxt-link>
                </li>
                <li>
                    <i class='bx bxs-dashboard'></i>
                    <p>Contas a Receber</p>
                    <nuxt-link to="/administrator/incoming"></nuxt-link>
                </li>
                <li>
                    <i class='bx bxs-dashboard'></i>
                    <p>Contas a Pagar</p>
                    <nuxt-link to="/administrator/bill"></nuxt-link>
                </li>
                <li>
                    <i class='bx bxs-dashboard'></i>
                    <p>Fluxo de Caixa</p>
                </li>
                <li>
                    <i class='bx bxs-dashboard'></i>
                    <p>Configurações</p>
                </li>
                <li>
                    <i class='bx bxs-dashboard'></i>
                    <p>Perguntas Frequentes</p>
                </li>
                <li>
                    <i class='bx bxs-dashboard'></i>
                    <p>Suporte</p>
                </li>
            </ul>
            <div class="logout" :class="{active: isActive}">
                <div class="logout_user">
                    <i class='bx bx-user' ></i>
                    <div class="logout_user_content">
                        <h4>Lucas Costa</h4>
                        <p>Status</p>
                    </div>
                </div>
                <i title="Logout" class='bx bx-log-out-circle' ></i>
            </div>
          </div>
          <div class="main_content" :class="{active: isActive}">
              <nuxt/>
          </div>
    </div>
</template>

<script>
import Footer from '@/components/Footer.vue'

export default {
    data() {
        return {
            isActive: false
        }
    },
    methods: {
        switchValue() {
            this.isActive = !this.isActive
        },
        teste() {
            let obj = confirm("Deseja prosseguir?")
            console.log(obj, 'obj')
        }
    }
}
</script>

<style scoped>
.sidebar {
    position: fixed;
        top: 0;
        left: 0;
    height: 100%;
    width: 70px;
    background: #fff;
    /* padding: 6px 14px; */
    padding-bottom: 6px;
    box-shadow: 3px 3px 10px rgba(0, 0, 0, .1);
    /* border-right: 2px solid rgba(3, 8, 71, 1) ; */
    padding-right: 1px;
    transition: all .5s ease;
}

.sidebar.active {
    width: 240px;
    transition: .5s;
}

.logo_content {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 6px 14px;
    height: 60px;
    box-shadow: 3px 3px 10px rgba(0, 0, 0, .1);
}
.sidebar.active .logo_content {
    justify-content: space-between;
}

.logo_content .logo_text {
    font-weight: 300;
    display: none;
    -webkit-animation: fadeIn 1s forwards;
    animation: fadeIn 1s forwards;
}
.sidebar.active .logo_content .logo_text {
    display: block;
}

.logo_content .bx-menu {
    cursor: pointer;
    font-size: 1.3rem;
}

/*pages_title*/

.pages_title {
    text-align: center;
    margin: 20px 0;
    padding: 20px 5px;
}
.pages_title.active {
    text-align: center;
    margin: 20px 0;
    padding: 20px 0;
}

.pages_title h3 {
    position: relative;
    font-size: .8rem;
    font-weight: 300;
    text-transform: uppercase;
    transition: .3s ease;
    padding: 0 5px;
}
.pages_title.active h3{
    font-size: 1rem;
}

.pages_title h3::before {
    content: '';
    position: absolute;
        bottom: -10px;
        left: 50%;
    transform: translateX(-50%);
    height: 3px;
    width: 50%;
    background: goldenrod;
}

/*ul*/

li {
    position: relative;
    cursor: pointer;
    margin-bottom: 9px;
    border-radius: 4px;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 14px 12px;
    transition: .5s ease;
    box-shadow: 3px 3px 5px rgba(0, 0, 0, .1);
}
ul.active li {
    justify-content: flex-start;
    padding-left: 25px;
    padding-right: 0;
}

li:hover {
    background: black;
}
li:hover i {
    color: white;
}
li:hover p {
    color: white;
}

li p {
    display: none;
    -webkit-animation: fadeIn 1s forwards;
    animation: fadeIn 1s forwards;
}
ul.active li p{
    display: block;
}

li i {
    margin-right: 0;
}
ul.active li i {
    margin-right: 10px;
}

li a {
    position: absolute;
        top: 0;
        left: 0;
    width: 100%;
    height: 100%;
}

.nuxt-link-exact-active::before {
    content: '';
    position: absolute;
        top: 0;
        left: 0;
    width: 2%;
    height: 100%;
    background: goldenrod;
    border-top-right-radius: 2px;
    border-bottom-right-radius: 2px;
}

/*logout*/

.logout {
    position: absolute;
        bottom: 0;
    width: 70px;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 6px 12px;
    background: #f3f3f3;
}
.logout.active {
    justify-content: space-between;
    width: 240px;
}

.logout .logout_user {
    display: flex;
    align-items: center;
    justify-content: center;
}

.logout_user i {
    font-size: 18px;
    margin-right: 0px;
    padding: 8px;
    border: 1px solid rgba(0, 0, 0, .1);
    border-radius: 4px;
}
.logout.active .logout_user i {
    margin-right: 8px;
}

.logout_user_content {
    display: none;
    -webkit-animation: fadeIn 1s forwards;
    animation: fadeIn 1s forwards;
}
.logout.active .logout_user_content {
    display: block;
}

.logout_user .logout_user_content h4{
    font-weight: 400;
    font-size: .9rem;
    transition: .3s ease;
}

.logout_user .logout_user_content p {
    font-weight: 300;
    font-size: .7rem;
}

.logout .bx-log-out-circle {
    display: none;
    -webkit-animation: fadeIn 1s forwards;
    animation: fadeIn 1s forwards;
    cursor: pointer;
    font-size: 20px;
}
.logout.active .bx-log-out-circle {
    display: block;
}

@-webkit-keyframes fadeIn {
    from { opacity: 0; }
      to { opacity: 1; }
}
@keyframes fadeIn {
    from { opacity: 0; }
      to { opacity: 1; }
}

/**/

.main_content {
    position: absolute;
        left: 140px;
    height: 100%;
    width: calc(100% - 140px);
    transition: .3s ease;
    padding-top: 3%;
}

.main_content.active {
    left: 280px;
    width: calc(100% - 280px);
}
</style>