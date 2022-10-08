<template>
    <div class="administrator">
        <AppTitle
        titleStyle="style-1"
        titleText="Dashboard"
        />
        <AppTopBarDashboard/>
    </div>
</template>

<script>
import AppTopBarDashboard from '@/components/TopBar/AppTopBarDashboard.vue'
import AppTitle from '@/components/UI/AppTitle.vue'
import AppTable from '@/components/Tables/AppTable.vue'

export default {
    components: {
        AppTopBarDashboard,
        AppTitle,
        AppTable
    },
    layout: 'admin'
}
</script>