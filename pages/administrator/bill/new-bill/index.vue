<template>
    <div class="new-incoming">
        <AppTitle
        titleStyle="style-1"
        titleText="Pago"
        />
        <div class="rows">
            <AppFormBills/>
        </div>
    </div>
</template>

<script>
import AppTitle from '@/components/UI/AppTitle.vue'
import AppIcon from '~/components/UI/AppIcon.vue'
import AppFormBills from '@/components/Forms/AppFormBills.vue'

export default {
    components: {
        AppTitle,
        AppIcon,
        AppFormBills
    },
    layout: 'admin'
}
</script>

<style scoped>
.new-incoming {
    position: relative;
    padding-bottom: 10px;
}

/* .rows {
    display: grid;
    grid-template-columns: 1fr 1fr;
} */
</style>