<template>
    <div class="flex-cl">
        <div>
            <span style="font-weight: 600;">Id</span> : <span>{{ campaignDetails.id }}</span>
        </div>
        <div>
            <span style="font-weight: 600;">Sub Domain</span> : <span>{{ campaignDetails.sub_domain }}</span>
            {{ campaignDetails.sub_domain }}
        </div>
        <div>
            <span style="font-weight: 600;">Campaign Type</span> : <span>{{ campaignDetails.campaign_type }}</span>
        </div>
        <div>
            <span style="font-weight: 600;">Email</span> : <span>{{ campaignDetails.email }}</span>
        </div>
    </div>
</template>
<script>
export default {
    props: {
        campaignDetails: {
            type: Object,
            default:() => {},

        }
    }   
}
</script>

<style scoped>
.flex-cl {
    margin: 30px;
}
</style>

