<template>
    <view>
        <form @submit="getWife" @reset="formReset">
<!--            <view>实时获取输入值：{{inputValue}}</view>-->
            <view>
                <input class="weui-inpu" maxlength="10" @input="bindKeyInput" placeholder="输入同步到view中"/>
            </view>
            <button form-type="submit" size="mini" type="primary"> 随便来个老婆</button>
            <button form-type="reset" size="mini" type="primary"> 清空</button>
        </form>
    </view>
</template>

<script>
    export default {
        name: "ViaNumber",
        data() {
            return {
                inputValue: 2333,
            }
        },
        methods: {
            bindKeyInput: function (e) {
                this.inputValue = e.detail.value;
            },
            getWife: function () {
                this.$emit('numberChange', this.inputValue);
                console.log('更改cardID 传回index为'+this.inputValue);
            },

        }

    }
</script>

<style lang="scss">
    .weui-input {
        height: 2.58823529em;
        min-height: 2.58823529em;
        line-height: 2.58823529em;
    }
</style>