<template>
    <div class="app-container">
        <notice :value="true" :data="noticeData"></notice>
    </div>
</template>

<script>
    import Notice from  './Notice.vue';
    export default {
        name: "Notice.demo.vue",
        components: {
            'notice': Notice
        },
        data() {
            return {
                noticeData: {
                    id: 1,
                    typeCn: '加分',
                    text: '购险成功！五月已提升25车主分！'
                }
            }
        }
    }
</script>

<style scoped>

</style>
