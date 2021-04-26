<template>
    <div class="block">
        <div style="float:left;">
            <h1>Base</h1>
            <h1>{{ base }}</h1>
        </div>
        <div style="float:right;">
            <textarea class="scroll input_area" @keyup="convertToBase10($event, base)" @keypress="validateNum($event, base)" :value="showByBase(base)" @blur="resetCurrent()" />
        </div>
    </div>

</template>

<script>
export default {
    name: "InputBlock",
    props: {
        base: Number,
        valueNum: BigInt
    },
    emits: ['onValueChange'],
    data() {return{
        currentBase: 0,
        currentText: ""
    }},
    methods: {
        validateNum(e, base){
            var checkParse = parseInt(e.key, base);

            if(isNaN(checkParse))
                e.preventDefault();
        },

        convertToBase10(e, base){
            if(e.target.value === ""){
                this.changeValueNum(null)
            } else {
                var d;
                d = this.parseBigInt(e.target.value, base)
                this.changeValueNum(d)
                console.log(d)
            }
            this.currentBase = base
            this.currentText = e.target.value
        },

        showByBase(base){

            return this.valueNum != null ? base == this.currentBase ? this.currentText : this.valueNum.toString(base) : ""
            
        },

        resetCurrent(){
            console.log(this.valueNum)
            this.currentBase = 0,
            this.currentText = ""
        },

        changeValueNum(num) {
            this.$emit('onValueChange', num)
        },

        parseBigInt(str, base=10) {
            var bigint = BigInt(0)
            for (var i = 0; i < str.length; i++) {
                var code = str[str.length-1-i].charCodeAt(0) - 48; if(code >= 10) code -= 39
                var pow = this.powBigInt(BigInt(base),i)
                var rr = pow * BigInt(code)
                bigint += rr
                if(base == 10){
                    console.log(base + ' '+ i + ' '+ pow + ' ' + code + ' ' + rr)
                }
            }
            return bigint
        },

        powBigInt(num, expo){
            var result = BigInt(1)
            for (var i = 0; i < expo; i++) {
                result = result * num
            }

            return result
        }
    }
}
</script>

<style scoped>
    .block {
        border-color: #000;
        border-style: groove;
        border-radius: 2px;
        box-shadow: 0 10px 10px -5px #000;
        width: 300px;
        padding: 20px;
        overflow: auto;
    }

    .scroll::-webkit-scrollbar {
        display: none;
    }

    .input_area{
        padding: 0.2em;
        font-size:40px;
        width:4.5em;
        height:4em;
        resize:none;
        text-transform: uppercase
    }
</style>