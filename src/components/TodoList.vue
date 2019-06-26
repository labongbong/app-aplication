<template>
    <div>
        <transition-group tag="ul" name="todo">
            <li v-for="(todoItem, index) in todolist" v-bind:key="index">
                <span>{{ todoItem }}</span>
                <button v-on:click="removeTodoItem(todoItem, index)">remove</button>    
            </li>
        </transition-group>
    </div>
</template>

<script>
export default {
    props: ['todolist'],

    // data() {
    //     return {
    //         todoItems: [],
    //     }
    // },
    methods: {
        // fetchTodoItems: function(){
        //     for(var i = 0; i<localStorage.length; i++){
        //         var item = localStorage.key(i);
        //         this.todoItems.push(item);
        //     }
        // },
        removeTodoItem: function(todo, index){
            console.log('deleted', todo, index);
            this.$emit('remove', todo, index);
            // this.todoItems.splice(index,1);
            // localStorage.removeItem(todo);
        },
    },
    // created: function(){ // vue로 instance 생성하고 로딩될때 컴포넌트가 생성되자마자 실행되는 로직
    //     this.fetchTodoItems();
    // }

};

</script>

<style>
.todo-item {
  display: inline-block;
  margin-right: 10px;
}
.todo-enter-active, .todo-leave-active {
  transition: all 1s;
}
.todo-enter, .todo-leave-to /* .todo-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}
</style>
