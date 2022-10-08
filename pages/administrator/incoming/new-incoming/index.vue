<template>
    <div class="new-incoming">
        <AppTitle
        titleStyle="style-1"
        titleText="Recebido"
        />
        <div class="rows">
            <AppFormIncoming/>
        </div>
    </div>
</template>

<script>
import AppTitle from '@/components/UI/AppTitle.vue'
import AppIcon from '~/components/UI/AppIcon.vue'
import AppFormIncoming from '@/components/Forms/AppFormIncoming.vue'
import AppTableNewIncoming from '@/components/Tables/AppTableNewIncoming.vue'

export default {
    components: {
        AppTitle,
        AppIcon,
        AppFormIncoming,
        AppTableNewIncoming
    },
    layout: 'admin'
}
</script>

<style scoped>
.new-incoming {
    position: relative;
    padding-bottom: 10px;
}
</style>