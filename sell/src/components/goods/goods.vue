<template>
    <div class="goods">
        <div class="menu-wrapper"></div>
        <div class="foods-wrapper"></div>
    </div>
</template>

<script type="text/ecmascript-6">
    const ERR_OK = 0;

    export default {
        props: {
            seller: {
                type: Object
            }
        },
        data() {
            return {
                goods: []
            };
        },
        created() {
            this.$http.get('/api/goods').then((respones) => {
                respones = respones.body;
                if (respones.errno === ERR_OK) {
                    this.goods = respones.data;
                    console.log(this.goods);
                }
            });
        }
    };
</script>

<style lang="stylus" rel="stylesheet/stylus">
    .goods
        display: flex
        position: absolute
        top: 176px
        bottom: 40px
        width: 100%
        .menu-wrapper
            flex: 0 0 80px
            width: 80px
        .foods-wrapper
            flex: 1
</style>
