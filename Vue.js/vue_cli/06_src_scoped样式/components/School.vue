<template>
    <div class="demo">
        <h2 class="title">学校名称：{{ name }}</h2>
        <h2>学校地址：{{ address }}</h2> 
    </div>
</template>
<script>
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'School',
    data() {
        return {
            name: 'Hubei University of Art and Science',
            address: 'Hubei XiangYang'
        }
    }
}
</script>

<style scoped>
    .demo {
        background-color: skyblue;
    }
</style>