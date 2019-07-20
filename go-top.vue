<template>
    <div class="page-to-top" v-show="visible" @click="toTop"></div>
</template>

<script>

    const _height = window.innerHeight || window.screen.height;
    // 去顶部
    export default {
        name: "go-top",
        data() {
            return {
                visible: false
            }
        },
        mounted() {
            window.addEventListener('scroll', this.handleScroll);
            window.addEventListener('touchmove', this.handleScroll)
        },
        beforeDestroy() {
            window.removeEventListener('scroll', this.handleScroll);
            window.removeEventListener('touchmove', this.handleScroll)

        },
        methods: {
            handleScroll() {
                this.visible = window.scrollY > 1.5 * _height;

            },
            toTop() {
                window.scrollTo(0, 0);
            }
        }
    }
</script>

<style scoped>
    .page-to-top {
        position: fixed;
        bottom: 3rem;
        right: .6rem;
        border-radius: 1.6rem;
        width: 1.6rem;
        height: 1.6rem;
        background: url(data:image/png;charset=utf-8;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAmBAMAAAAhNzZRAAAABGdBTUEAALGPC/xhBQAAAB5QTFRFAAAA////////////////////////////AAAA////1NnxJAAAAAl0Uk5TAN3zXsMyFZ8Alc3kwAAAAKlJREFUKM9jmIkKGND5xAFW4wAUfuTMqchcNsnyiQlI/JTpDJViSHxPN4aUKQguO1Axm2QBnF+pCiSCpsOlZ4IsY9WEKYicDKYsoVayKkEk2CdB3JQI0wixks3TAcpnmZIAtQzqSk+Qxko1uL1J0xGmMECttFRGcrflZIZKAyQ+83QGS1CoTQCyOUGMyQzMnkj8KRDFnBNgBMOw4LOAk4oDIpxAfp4CDjcAxtdL76lU1wEAAAAASUVORK5CYII=) center no-repeat #5b6167;
        background-size: .6rem .76rem;
        z-index: 100;
    }
</style>
