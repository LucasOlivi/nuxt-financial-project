<template>
    <div class="incoming">
        <AppTitle
        titleStyle="style-1"
        titleText="Contas a Pagar"
        />
        <AppTopBarDashboard/>
        <AppTopBar
        redirect="/administrator/bill/new-bill"
        />
        <AppTable
        isShown="true" 
        />
    </div>
</template>

<script>
import AppTopBarDashboard from '@/components/TopBar/AppTopBarDashboard.vue'
import AppTitle from '@/components/UI/AppTitle.vue'
import AppTable from '@/components/Tables/AppTable.vue'
import AppTopBar from '@/components/TopBar/AppTopBar.vue'

export default {
    components: {
        AppTopBarDashboard,
        AppTitle,
        AppTable,
        AppTopBar
    },
    layout: 'admin'
}
</script>