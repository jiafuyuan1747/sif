<template>
    <view class="content">
        <!--		<head-one></head-one>-->
<!--        <cards-info :cardID="cardID" ></cards-info>-->
        <Via-Number @numberChange="handleNumberChange"></Via-Number>
        <img :src="src" alt=""  mode="widthFix">
    </view>
</template>

<script>
    import headOne from "../../components/headOne";
    import cardsInfo from "../../components/cardsInfo";
    import ViaNumber from "../../components/ViaNumber";

    export default {
        components: {
            headOne,
            ViaNumber,
            cardsInfo //第二步，注册组件
        },
        data() {
            return {
                title: 'SifCard',
                cardID: 1004,
                componentKey: 0,
                src: "https://images.weserv.nl/?url=https://www.lovelivesupport.com/asset/assets/image/units/u_normal_navi_33105001.png",
            }
        },
        onLoad() {
        },
        created() {
        },
        mounted() {
        },
        methods:{
            handleNumberChange:function (number) {
                this.cardID = number;
                console.log(`index接收到传来的cardID为${number},将它赋值给this.cardID：${this.cardID}`);
                let that = this;
                wx.request({
                    url: `https://www.lovelivesupport.com/api.php/card/cn/info/${this.cardID}`, //仅为示例，并非真实的接口地址
                    header: {
                        'content-type': 'application/json' // 默认值
                    },
                    success (res) {
                        console.log(res.data);
                        const normalCardID = res.data.response.card_info.normal_card_id;
                        that.src = `https://images.weserv.nl/?url=https://www.lovelivesupport.com/card/v4/${normalCardID}.png`;
                        // console.log(res.data.response.card_nor_navi.unit_navi_asset);
                        // that.src  =  'https://images.weserv.nl/?url='
                        //     + 'https://www.lovelivesupport.com/asset/'
                        //     + res.data.response.card_max_navi.unit_navi_asset;
                    }
                });
                console.log(this.src);
            },
		},

    }
</script>

<style lang="scss">
    .content {
        text-align: center;
        display: flex;
        flex-wrap: wrap;
    }

    .title {
        font-size: 36 rpx;
        color: #8f8f94;
    }
</style>
