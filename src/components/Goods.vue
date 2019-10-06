<template>
    <div class="goods">
        <GoodsItem v-for="(item, id) in items"
                   :item="item"
                   :classProp="id % 6 === 0 ? 'two-row' : ''">
        </GoodsItem>
    </div>
</template>

<script>
    import GoodsItem from './GoodsItem';

    export default {
        name: "Goods",
        components: {GoodsItem},
        data(){
            return {
                items: []
            };
        },
        mounted(){
            fetch(
                'http://192.168.64.2/api/subcategory.php',
                {
                    method: 'GET',
                    headers: {
                        'Content-Type': 'application/json'
                    }
                }
            ).then(res => res.json()).then(res => {
                this.items = res;
            });
        }
    }
</script>

<style scoped>
    .goods{
        display: flex;
        flex-wrap: wrap;
    }
</style>