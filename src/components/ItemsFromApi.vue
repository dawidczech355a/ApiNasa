<template>
    <div class="printPhoto">
        <img :src="photo" :alt="title">
    </div>    
</template>

<script>
export default {
    name: 'ItemsFromApi',
    props: {
        item: {
            type: Object,
            required: true,
        },
    },
    
    data() {
        return {
            photo: this.item.links[0].href,
            title: this.item.data[0].title,
        };
    },
};
</script>

<style lang="scss" scoped>
    .printPhoto {
        width: 230px;
        height: 170px;
        transform: translate(15%, 10%);
        margin-bottom: 15px;
        
        img {
            width: 100%;
            height: 100%;
            cursor: pointer;
        }
        img:hover {
            width: 250px;
            height: 180px;
            transform: translate(-4%, -3%);
        }
    }
</style>
