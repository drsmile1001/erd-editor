<template>
    <div>
        <h1>ERD 編輯器</h1>
        <div class="area">
            <svg width="100%"
                 height="100%">
            </svg>
            <svg-entity v-for="(entity,idx) in entities"
                        :key="idx"
                        :entity="entity"/>
        </div>
    </div>
</template>

<script>
import svgEntity from "./svg-entity"
export default {
    components: {
        "svg-entity": svgEntity
    },
    data() {
        return {
            entities: [
                {
                    name:"AA",
                    position:{
                        x:400,
                        y:400,
                    },
                    width: 400,
                    height: 400,
                    items: [
                        {
                            field: "Id",
                            type: "Guid"
                        },
                        {
                            field: "Name",
                            type: "string"
                        }
                    ]
                },
                {
                    name:"BB",
                    position:{
                        x:400,
                        y:400,
                    },
                    width: 400,
                    height: 400,
                    items: [
                        {
                            field: "Id",
                            type: "Guid"
                        },
                        {
                            field: "Phone",
                            type: "string"
                        }
                    ]
                }
            ],
        }
    },
    methods: {
        
    }
}
</script>

<style>
.area {
    position: relative;
    width: 1280px;
    height: 720px;
    overflow: hidden;
}
svg {
    position: absolute;
    background: lightblue;
}
</style>
