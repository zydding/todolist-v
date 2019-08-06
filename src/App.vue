<template>
  <div id="app">
    <h1>TodoList</h1>
    <addNew @submitNewItem = "addNewItem"></addNew>
    <thelist @handleJudge = "toDone" title = "toDo" v-bind:List = "todoList"></thelist>
    <thelist @handleDelete = "toDelete" title = "Done" v-bind:List = "doneList" :ListType = "true"></thelist>
    
  </div>
</template>

<script>
import addNew from './components/addNew';
import thelist from './components/theList';

export default {
  name: 'app',
  data(){
    return {
      todoList:[],
      doneList:[]
    }
  },
  methods:{
    addNewItem: function(newItem){
      this.todoList.push(newItem);
    },
    toDone: function(index){
      this.doneList.push(this.todoList.splice(index,1)[0]);
    },
    toDelete: function(index){
      this.doneList.splice(index,1);
    }
  },
  components: {
    addNew,
    thelist
  }
}
</script>