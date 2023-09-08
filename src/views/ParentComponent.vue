<template>
<child-component-new-vue :loaderBoxCount="loaderBoxCount"></child-component-new-vue>
</template>
<script>
import ChildComponentNewVue from '@/components/ChildComponentNew.vue'

export default {
    data: function() {
        return {
            loaderBoxCount: 7,
        }
    },
    components:{
        ChildComponentNewVue,
    }
}

</script>
