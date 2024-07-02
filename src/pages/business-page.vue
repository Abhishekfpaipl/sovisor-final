<template>
    <div>
        <div class="my-5">
            <ServicesFormBanner />
        </div>
        <div class="">
            <BusinessCard />
        </div>
    </div>
</template>
<script>
import ServicesFormBanner from "@/components/services/FormBanner.vue";
import BusinessCard from "@/components/BusinessCard.vue";
export default {
    name:"BusinessPage",
    components:{
        ServicesFormBanner,
        BusinessCard,
    }
}
</script>
<style lang="">

</style>