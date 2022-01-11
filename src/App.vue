<template>
  <div id="app">
      <TodoHeader></TodoHeader>
      <TodoInput v-on:addTodo="addTodo"> </TodoInput>
      <TodoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></TodoList>
      <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>


</template>
  <script>
    import TodoHeader from './components/TodoHeader.vue'
    import TodoInput from './components/TodoInput.vue'
    import TodoList from './components/TodoList.vue'
    import TodoFooter from './components/todoFooter.vue'

    export default{
      components: {
          // 컴포넌트 이름 : 컴포넌트 내용
          'TodoHeader' : TodoHeader,
          'TodoInput' : TodoInput,
          'TodoList' : TodoList,
          'TodoFooter' : TodoFooter,
       },
       data(){
         return{
           //TodoList컴포넌트에 props로 전달할 data
           todoItems: []
         }
       },
       methods:{
         addTodo(todoItem){
           //로컬 스토리지에 데이터를 추가하는 로직
           // 입력받은 텍스트를 로컬 스토리지의 setItem()API를 이용하여 저장
           // API형식은 키,값 형태이며 저장 기능을 단순하게 하기 위해 키,값 모두 입력받은 텍스트로 지정
           localStorage.setItem(todoItem, todoItem);
           this.todoItems.push(todoItem);
         },
         clearAll(){
            localStorage.clear();
            this.todoItems = [];
         },
        removeTodo(todoItem, index) {
          //localStorage에서 키에 해당하는 값을 제거
          localStorage.removeItem(todoItem);
          //splice(배열의 변경을 시작할 인덱스, 배열에서 제거할 요소의 수)
          this.todoItems.splice(index, 1);
        }
       },
      created(){
          if(localStorage.length > 0){
              for(var i=0;i<localStorage.length;i++){
                  this.todoItems.push(localStorage.key(i));
              }
          }
      }

    }
  </script>
  <style>
     body{
       text-align: center;
       background-color: #f6f6f8;
       
     }
     input{
       border-style: groove;
       width: 200px;
     }
     button{
       border-style: groove;
     }
     .shadow{
       box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
     }
  </style>s
