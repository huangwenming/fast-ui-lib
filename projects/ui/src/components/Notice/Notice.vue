<template>
    <div class="notice-item" :value="value" v-show="visible">
        <span class="title">{{data.typeCn}}</span>
        <div class="desc" @click="goToUrl">{{data.text}}</div>
        <div class="close" @click="close"></div>
    </div>
</template>

<script>
    export default {
        name: 'Notice',
        props: ['value', 'data'],
        data() {
            return {
                visible: false,
            }
        },
        mounted() {
            this.visible = this.value;
        },
        methods: {
            close() {
                let me = this;
                let item = document.querySelector('.notice-item');
                item.className += " " + 'animation-dispear';
                // 动画500毫秒后完成，此时关闭提醒条
                setTimeout(function () {
                    me.visible = false;
                }, 500);
                this.$emit('close');
            },
            goToUrl() {
                this.$emit('click');
            }
        },
        watch:{
            value(val) {
                this.visible = val;
            },
            visible(val) {
                this.$emit('input', val);
            }
        }
    }
</script>

<style>
    .notice-item {
        width: 100%;
        height: 90px;
        background-color: #fff;
        overflow: hidden;
        display: flex;
        align-items:center;
    }
    .notice-item .title {
        width: 60px;
        padding: 4px 0 4px 0;
        margin-left: 30px;
        color: #ee2630;
        font-size: 20px;
        text-align: center;
        border: 1px solid #ee2630; /* no */
        border-radius: 6px;
    }
    .notice-item .desc {
        width: 78%;
        color: #333;
        font-size: 28px;
        padding-left: 10px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
    }
    .notice-item .close {
        width: 30px;
        height: 30px;
        background: url("../../assets/images/close-gray.png") no-repeat;
        background-size: 30px 30px;
    }
    .animation-dispear {
        animation: dispear-line 0.5s linear 0s;
    }
    @keyframes dispear-line {
        0% {
            height: 90px;
        }
        100% {
            height: 0;
        }
    }
</style>
