<template>
    <transition name="el-fade-in-linear">
        <div class="winShow" @click="close" v-if="showWin">
            <i class="el-icon-circle-close"></i>
            <div class="box">
                <img v-if="img" :src="img" alt="">
                <div v-else class="no-data">
                    无图片
                </div>
            </div>
        </div>
    </transition>
</template>

<script>
export default {
    data() {
        return {
            showWin: false
        }
    },
    props: ['show','img'],
    methods: {
        close() {
            this.showWin = false
        },
        toShow() {
            this.showWin = true
        }
    },
    watch: {
        show() {
            this.showWin = !this.showWin
        }
    }
};
</script>

<style lang="scss" scoped>
    .winShow {
        position: fixed;
        z-index: 99999;
        top: 0px;
        left: 0px;
        height: 100%;
        width: 100%;
        background: rgba(0,0,0,.4);
        i {
            z-index: 10;
            cursor: pointer;
            color: rgba(255,255,255,.7);
            font-size: 50px;
            position: absolute;
            right: 20px;
            top: 10px;
            transition: all .4s ease;
            transform: rotate(0deg);
            &:hover {
                transform: rotate(180deg);
                color: rgba(255,255,255,1);
            }
        }
        .box {
            position: relative;
            max-width: 1260px;
            height: 100%;
            margin: 0 auto;
            img {
                position: relative;
                top: 50%;
                left: 50%;
                transform: translate(-50%,-50%);
                max-width: 100%;
                max-height: 90%;
            }
            .no-data {
                position: relative;
                top: 50%;
                left: 50%;
                transform: translate(-50%,-50%);
                width: 160px;
                height: 70px;
                line-height: 70px;
                text-align: center;
                font-size: 20px;
                border-radius: 22px;
                letter-spacing: 6px;
                color: #fff;
            }
        }
    }
</style>
