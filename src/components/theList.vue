<template>
    <div class="card">
        <h5 class="card-header">{{title}}</h5>
        <div class="card-body">
            <ul class="list-group">
                <li class="list-group-item" :class='typeClass' v-for="(item,index) in List" :key = "index" @click='judgeItem(index)'>{{item}}</li>
            </ul>
        </div>
    </div>    

</template>

<script>
    export default {
        name:'thelist',
        props:{
            List:{
                type:Array,
                required:true,
            },
            ListType:{
                type:Boolean,
                default:false,
            },
            title:[String,Number]
        },
        computed:{
            typeClass(){
                return {'list-group-item-danger':!this.ListType,
                    'list-group-item-success':this.ListType}
            }
        },
        methods: {
            judgeItem:function(index){
                if(!this.ListType){
                    this.$emit("handleJudge",index);
                }else{
                    this.$emit("handleDelete",index);
                }
            }
        }
    }
</script>