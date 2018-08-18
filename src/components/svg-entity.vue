<template>
    <foreignObject :x="xx"
                   :y="yy"
                   :width="width"
                   :height="height"
                   @click="click">
        <table :focus="selected">
            <thead>
                <tr>
                    <th>欄位</th>
                    <th>型別</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(item,idx) in items"
                    :key="idx">
                    <td>{{item.field}}</td>
                    <td>{{item.type}}</td>
                </tr>
            </tbody>
        </table>
    </foreignObject>
</template>

<script>
export default {
    props: {
        x: Number,
        y: Number,
        width: Number,
        height: Number,
        items: Array,
        selected:Boolean
    },
    computed: {
        xx() {
            return this.x - this.width / 2
        },
        yy() {
            return this.y - this.height / 2
        }
    },
    methods:{
        click(){
            this.$emit("click");
        }
    }
}
</script>

<style scoped>
table{
    width:100%;
    height: 100%;
    background-color: pink;
}
table[focus]{
    background-color: red;
}
</style>
