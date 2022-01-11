<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
             <i class="addBtn fa fa-plus" aria-hidden="true"></i>
        </span>
    </div>
</template>
<script>


export default({
    data(){
        return{
            newTodoItem: ''
        }
    },
    methods: {
        addTodo(){
            if(this.newTodoItem!==""){
            // console.log(this.newTodoItem);
            // trim은 string의 앞뒤 공백을 제거
            var value = this.newTodoItem && this.newTodoItem.trim();
            // this.#emit(하위컴포넌트의 이벤트명, 전달데이터)
            this.$emit('addTodo',value);
            this.clearInput();
            }
            /* 
            로컬 스토리지에 저장된 것을 확인하려면
            크롬 개발자 도구의 [Application -> Local Storage -> http://localhost:8080]
            */
        },
        
        clearInput(){
            this.newTodoItem = '';
        }
    }
})
</script>
<style>
    input:focus{
        outline: none;
    }
    .inputBox{
        background: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputBox input{
        border-style: none;
        font-size: 0.9rem;
    }
    .addContainer{
        float: right;
        background: linear-gradient(to right, #6478fb, #8763fb);
        display: inline-block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }
    .addBtn{
        color: white;
        vertical-align: middle;
    }
</style>
