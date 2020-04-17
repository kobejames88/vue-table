
<!-- :::demo 通过给 `columns` 设置 `isEdit:true` 开启单元格编辑。<br> **回调事件**： <br> - `cell-edit-done`回调函数，回调参数为 `newValue`、`oldValue`、`rowIndex`、`rowData`、`field`，并给`table-data`当前编辑的列赋值 <br> **提示**：由于直接通过操作DOM 会破坏响应式，通过在`cell-edit-done`回调函数中给 `table-data`编辑的列赋值，达到响应式的目的

```html -->
<template>
    <v-table
            is-horizontal-resize
            style="width:100%"
            :columns="columns"
            :table-data="tableData"
            row-hover-color="#eee"
            row-click-color="#edf7ff"
            :cell-edit-done="cellEditDone"
    ></v-table>
</template>

<style>
    .cell-edit-color{
        color:#2db7f5;
        font-weight: bold;
    }
</style>

<script>

    export default{
        data() {
            return {
                  tableData: [
                        {"name":"AAREN","tel":"1300.00","hobby":"14590.00","address":"23123.00"},
                        {"name":"AGATHA","tel":"1500.00","hobby":"1459.00","address":"23120.00"},
                        {"name":"ANDERSON","tel":"1600.00","hobby":"13212.00","address":"4141.00"},
                        {"name":"ANGELINA","tel":"1700.00","hobby":"123123.00","address":"4546.00"},
                        {"name":"ANNABELLA","tel":"1800.00","hobby":"12312.00","address":"41341.00"}
                     ],
                    columns:  [
                             {field: 'name', title:'name', width: 80, titleAlign: 'center',columnAlign:'center',isEdit:true,
                              formatter: function (rowData,rowIndex,pagingIndex,field) {

                                   return `<span class='cell-edit-color'>${rowData[field]}</span>`;
                               },isResize:true},
                             {field: 'tel', title: 'save', width: 150, titleAlign: 'center',columnAlign:'center',isEdit:true,isResize:true},
                             {field: 'hobby', title: 'loan', width: 150, titleAlign: 'center',columnAlign:'center',isEdit:true,isResize:true},
                             {field: 'address', title: 'debt', width: 280, titleAlign: 'center',columnAlign:'center',isEdit:true,isResize:true}
                     ]
            }
        },
        methods:{

            // 单元格编辑回调
            cellEditDone(newValue,oldValue,rowIndex,rowData,field){

                this.tableData[rowIndex][field] = newValue;

                // 接下来处理你的业务逻辑，数据持久化等...
            }
        }
    }
</script>
```
:::

