<template>
    <div>
        <div class="input-group mb-3">
                <div class="input-group-prepend">
                <span class="input-group-text">请输入待办事项</span>
            </div>
            <input type="text" class="form-control" v-model="newItem" aria-label="Amount (to the nearest dollar)">
                <div class="input-group-append">
                <span class="input-group-text" @click='handleAdd'>添加</span>
            </div>
        </div> 

    </div>
</template>

<script>    
export default {
    name:'addNew',
    data(){
        return {
            newItem:""
        }
    },
    methods:{
        handleAdd:function(){
            if(this.newItem == ""){
                return;
            }
            this.$emit('submitNewItem',this.newItem);
            this.newItem = "";
        }
    }
}
</script>