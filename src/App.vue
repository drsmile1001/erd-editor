<template>
    <div>
        <h1>ERD 編輯器</h1>
        <svg ref="svg"
             width="1280"
             height="720"
             @mousemove="event">
            <svg-entity v-for="(entity,idx) in entities"
                        :key="idx"
                        :x="entity.x"
                        :y="entity.y"
                        :width="entity.width"
                        :height="entity.height"
                        :items="entity.items"
                        :selected="entity === selected"
                        @click="switchSelect(entity)" />
        </svg>
    </div>
</template>

<script>
import svgRect from "./components/svg-rect"
import svgEntity from "./components/svg-entity"
export default {
    components: {
        "svg-rect": svgRect,
        "svg-entity": svgEntity
    },
    data() {
        return {
            entities: [
                {
                    x: 100,
                    y: 100,
                    width: 200,
                    height: 100,
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
                    x: 300,
                    y: 300,
                    width: 200,
                    height: 100,
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
            selected:null
        }
    },
    methods: {
        switchSelect(entity){
            console.log(entity);
            this.selected = this.selected === entity
            ? null
            : entity;
        },
        event(e) {
            if(!this.selected) return;
            
            var rect = this.$refs.svg.getBoundingClientRect()
            var x = e.clientX - rect.left
            var y = e.clientY - rect.top
            this.selected.x = x
            this.selected.y = y
        }
    }
}
</script>

<style>
svg {
    background: lightblue;
}

</style>
