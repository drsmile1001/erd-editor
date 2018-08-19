<template>
    <div class="entity" @mousemove="mousemove">
        <el-card>
            <div slot="header" @mousedown="mousedown"
                                   @mouseup="mouseup">
                <el-row >
                    <el-col :span="24">
                        <span>{{entity.name}}</span>
                    </el-col>
                </el-row>

            </div>
            <el-table :data="entity.items">
                <el-table-column prop="field"
                                 label="欄位">
                </el-table-column>
                <el-table-column prop="type"
                                 label="型別">
                </el-table-column>
            </el-table>
        </el-card>
    </div>

</template>

<script>
export default {
    props: {
        entity: Object
    },
    data() {
        return {
            dragging: false,
            dragData: null
        }
    },
    computed: {
        style() {
            return {
                top: `${this.entity.position.y - this.entity.height / 2}px`,
                left: `${this.entity.position.x - this.entity.width / 2}px`,
                width: `${this.entity.width}px`,
                height: `${this.entity.height}px`
            }
        }
    },
    methods: {
        mousedown(event) {
            this.dragData = {
                startX: this.entity.position.x,
                startY: this.entity.position.y,
                iniMouseX: event.clientX,
                iniMouseY: event.clientY
            }
            return false
        },
        mousemove(event) {
            if (!this.dragData) return
            const dx = event.clientX - this.dragData.iniMouseX
            const dy = event.clientY - this.dragData.iniMouseY
            this.entity.position = {
                x: this.dragData.startX + dx,
                y: this.dragData.startY + dy
            }
            this.$el.style.top = `${this.entity.position.y -
                this.entity.height / 2}px`
            this.$el.style.left = `${this.entity.position.x -
                this.entity.width / 2}px`
            return false
        },
        mouseup() {
            this.dragData = null
            return false
        }
    },
    mounted() {
        this.$el.style.width = `${this.entity.width}px`
        this.$el.style.height = `${this.entity.height}px`
        this.$el.style.top = `${this.entity.position.y -
            this.entity.height / 2}px`
        this.$el.style.left = `${this.entity.position.x -
            this.entity.width / 2}px`
    }
}
</script>

<style>
.entity {
    position: absolute;
    background-color: pink;
}
.entity .el-card {
    width: 100%;
    height: 100%;
}
.entity .el-card .el-table {
    width: 100%;
    height: 100%;
}
.entity .el-card .el-card__header,
.entity .el-card .el-card__body {
    padding: 0px;
}
.entity .el-card .el-table td,
.entity .el-card .el-table th {
    padding: 0px;
}
</style>
