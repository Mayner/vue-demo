<template>
    <div class="header">
        <div class="content-wrapper">
            <div class="avatar">
                <img width="64" height="64" :src="seller.avatar" alt="">
            </div>
            <div class="content">
                <div class="title">
                    <div class="brand"></div>
                    <div class="name">{{seller.name}}</div>
                </div>
                <div class="description">
                    {{seller.description}}/{{seller.deliveryTime}}分钟送达
                </div>
                <div v-if="seller.supports" class="support">
                    <span class="icon" :class="classMap[seller.supports[0].type]"></span>
                    <span class="text">{{seller.supports[0].description}}</span>
                </div>
            </div>
        </div>
        <div class="bulletin-wrapper"></div>
    </div>
</template>

<script>
    export default {
        props: {
            seller: {
                type: Object
            }
        },
        created() {
            this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee'];
        }
    };
</script>

<style lang="stylus" rel="stylesheet/stylus">
@import "../../common/stylus/mixin"
    .header
        color: rgb(255, 255, 255)
        background: rgba(7, 17, 27, 0.5)
        .content-wrapper
            padding: 24px 12px 18px 24px
            font-size: 0
            .avatar
                display: inline-block
                margin-right: 16px
                vertical-align: top
                img
                    border-radius: 2px
            .content
                display: inline-block
                .title
                    font-weight: bold
                    line-height: 18px
                    .brand
                        display: inline-block
                        vertical-align: top
                        width: 30px
                        height: 18px
                        bg-image('brand')
                        background-size: 30px 18px
                        background-repeat: no-repeat
                    .name
                        display: inline-block
                        margin-left: 6px
                        font-size: 16px
                .description
                    margin: 8px 0 10px
                    font-size: 12px
                .support
                    .icon
                        display: inline-block
                        width: 12px
                        height: 12px
                        vertical-align: top
                        &.decrease
                            bg-image('decrease_1')
                        &.discount
                            bg-image('discount_1')
                        &.guarantee
                            bg-image('guarantee_1')
                        &.invoice
                            bg-image('invoice_1')
                        &.special
                            bg-image('special_1')
                        background-size: 12px 12px
                        background-repeat: no-repeat
                    .text
                        margin-left: 4px
                        font-size: 10px

</style>
