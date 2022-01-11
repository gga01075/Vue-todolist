<template>
    <div>
        <section>
            <ul>
               <li v-for="(todoItem,index) in propsdata" class="shadow" :key="index">
                   <i class="checkBtn fa fa-check" aria-hidden="true"></i>
                   {{todoItem}}
                   <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                   </span>
                   
              </li>
            </ul>
        </section>

    </div>
</template>
<script>
        /* 
          Todo리스트 리스트에 나타내기
            1단계 : 로컬 스토리지 데이터를 뷰 데이터에 저장
            2단계 : 뷰 데이터의 아이템 개수만큼 리스트 아이템 표시
        */

export default({
   props: ['propsdata'],

   methods: {
       /* 
       삭제기능
        1단계: 선택한 할일을 뷰에서 인식
        2단계: 선택한 할일을 로컬 스토리지에서 삭제
        3단계: 선택한 할일을 뷰 데이터에서 삭제 
       */
    removeTodo(todoItem, index) {
      this.$emit('removeTodo', todoItem, index);
    }
   },

})
</script>
<style>
    ul{
        list-style-type: none;
        padding-left: 0;
        margin-top: 0;
        text-align: left;
    }
    li{
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        padding: 0 0.9rem;
        background: white;
        border-radius: 5px;
    }
    .checkBtn{
        line-height: 45px;
        color: #62acde;
        margin-right: 5px;
    }
    .removeBtn{
        margin-left: auto;
        color: #de4343;
    }
</style>
