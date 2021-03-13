<template>
    <div v-for="base in lstBase" :key="base" style="padding:5px;text-align:left">
        <div style="display:inline-block">Base {{ base }} : </div>
        <div style="display:inline-block">
            <input  @keyup="convertToBase10($event, base)" @keypress="validateNum($event, base)" :value="showByBase(base)" on>
        </div>
    </div>

</template>

<script>
export default {
    name: "InputNumber",
    props: {
        lstBase: Array
    },
    data() {return{
        d: 1
    }},
    methods: {
        validateNum(e, base){
            var checkParse = parseInt(e.key, base);

            if(isNaN(checkParse))
                e.preventDefault();
        },

        convertToBase10(e, base){
            if(e.target.value === ""){
                this.d = null
            } else {
                this.d = parseInt(e.target.value, base)
            }
        },

        showByBase(base){
            return this.d != null ? this.d.toString(base) : ""
            
        },
    
    }
}
</script>

<style scoped>
    div input {
    text-transform: uppercase
    }
</style>