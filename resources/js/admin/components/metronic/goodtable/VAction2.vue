<template>
 <div class="details" @click="details(vprops.row)">
     <span class="text-success">details</span>
</div>
</template>

<script>
export default {
    props:["vprops"],
    methods:{
        details(row){
            this.$emit('details',row)
        }
    },
}
</script>

<style>
.details{
    cursor: pointer;
}
.details span:hover{
    color: red !important;
}
</style>