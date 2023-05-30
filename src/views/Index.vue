<template>
    <div class="index">
        <div class="c-wrap">
            <div class="select-wrap">
                <el-select ref="tempRef" v-model="selectedItems" multiple placeholder="请选择" style="width: 400px">
                    <el-option class="mul-add-select" v-for="item in selectionsList" :value="item.value" :label="item.label"
                        :key="item.value" :disabled="true"  @change="handleSelect">
                        <span style="float: left">{{ item.label }}</span>
                        <span style="float: right; color: #8492a6; font-size: 20px" @click="handleClick(item.value)">
                            <i class="el-icon-circle-plus-outline"></i>
                        </span>
                    </el-option>
                </el-select>
            </div>
            <div class="left-arrow-wrap">
                <el-button icon="el-icon-arrow-right" @click="handleAdd"></el-button>
            </div>
            <div class="selection-wrap">
                <div class="selection-wrap-title">
                    <div class="title">已选择</div>
                    <div class="close-btn" @click="handleClear">清空</div>
                </div>
                <div class="selections-items-content">
                    <div class="selection-item" v-for="(item, index) in selections" :key="'s' + item.value">
                        <div class="selection-item-title">{{ item.label }}</div>
                        <div class="selection-item-opt" @click="handleDelete(index)">
                            <i class="el-icon-close"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Index",
    data() {
        return {
            selectionsList: [
                {
                    label: "111",
                    value: "111",
                },
                {
                    label: "112",
                    value: "112",
                },
                {
                    label: "113",
                    value: "113",
                },
            ],
            selectedItems: [],
            selections: []
        }
    },
    methods: {
        handleSelect() {
        },

        handleClick(val) {
            this.$refs.tempRef.blur()
            this.selectedItems.push(val)
        },
        handleAdd() {
            const temp = this.selectionsList.filter(item => this.selectedItems.includes(item.value))
            this.selections = []
            this.selections.push(...temp)
            this.selectedItems = []
        },
        handleDelete(index) {
            this.selections.splice(index, 1)
        },
        handleClear() {
            this.selections = []
        }
    
    },
}
</script>
<style>
body {
    margin: 0;
    background-color: #ccc;
    font-size: 14px;
}

.mul-add-select.el-select-dropdown__item.is-disabled {
    color: #606266 !important;
    cursor: pointer !important;
}
</style>
<style scoped>
.c-wrap {
    box-sizing: border-box;
    padding: 20px;
    width: 1000px;
    height: 500px;
    background-color: #fff;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.selection-wrap {
    width: 300px;
    height: 400px;
}


.close-btn {
    cursor: pointer;
    color: #1989fa;
}

.selection-wrap-title {

    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 50px;
    padding: 0 10px;
    background-color: #f0f0f0;
    border-top-left-radius: 4px;
    border-top-right-radius: 4px;
}

.selection-wrap-title .title {
    font-weight: bold;
}

.selections-items-content {
    height: calc(100% - 50px);
    border: 1px solid #f0f0f0;
    border-top: none;
    border-bottom-left-radius: 4px;
    border-bottom-right-radius: 4px;
    padding: 12px;
}

.selection-item {
    margin-top: 12px;
    padding: 12px;
    background-color: #f0f0f0;
    border-radius: 4px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    cursor: pointer;
}

.selection-item:hover {
    box-shadow: 0 2px 12px 0 rgba(0, 0, 0, .1);
}

.selection-item-opt:hover {
    color: #1989fa;
}
</style>
