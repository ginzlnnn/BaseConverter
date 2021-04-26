<template>
<div style="width:80%;margin:auto;text-align:center">
    <div v-for="base in lstBase" :key="base" style="display:inline-block;margin:10px;" >
        <InputBlock :base=base :valueNum=valueNum @onValueChange="changeValueNum" />
    </div>
</div>

</template>

<script>

import InputBlock from './InputBlock.vue'

export default {
    name: "ResultPanel",
    components: {
        InputBlock
    },
    props: {
        lstBase: Array
    },
    data() {return{
        valueNum: BigInt(1),
        currentBase: 0,
        currentText: ""
    }},
    methods: {
        changeValueNum(num) {
            console.log(num)
            this.valueNum = num;
        }
    }
}
</script>