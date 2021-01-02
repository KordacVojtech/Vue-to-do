<template>
    <div class="table">
        <div class="tableNav">
            <div class="btns close"></div>
            <div class="btns minimize"></div>
            <div class="btns maximize"></div>
        </div>
        <div class="inputDiv">
            
                <input placeholder="Add a task..." class="input" v-model="message" name="message" >
                <button class="addBtn" @click="pushToArr">+</button>
            
        </div>
        <div class="outputDiv">
            <div class="output">
                <div v-show="todo.show" class="toDo" :key="todo" v-for="todo in toDos">
                    <h4 class="toDoItem">{{todo.message}}</h4>
                    <img v-if="!todo.completed" src="./check-mark.svg" class="checkMark" @click="todo.completed = !todo.completed">
                    <img v-else src="./delete.svg" class="checkMark" @click="todo.show = !todo.show">
                </div>
            </div>
            <button class="completeBtn" v-show="clearAllShow" @click="clearAll" >Mark all as complete</button>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            toDos: [],
            clearAllShow: false
        }
    },
    methods:{
        addToArr(){
            this.showDiv = !this.showDiv
        },
        changeCheck(){
            this.toDos.completed = !this.toDos.completed
        },
        pushToArr(){
            this.toDos.push({
                message: this.message,
                completed:false, 
                show:true
                });
                this.message ='',
                this.clearAllShow = true
                
        },
        clearAll(){
            this.toDos = this.toDos.length = 0,
            this.clearAllShow = false
        }
    }


}
</script>

<style scoped>
    .table{
        border: 1px solid rgb(167, 165, 165);
        width: 60rem;
        min-height: 40rem;
        border-radius: 4px;
        background-color: whitesmoke;
        box-shadow: 2px 5px 30px rgb(95, 95, 95);
        margin-top: 20px;
        border-top-left-radius: 5px;
        border-top-right-radius: 5px;
        
    }

    
    
    .tableNav{
        border: 1px solid rgb(97, 97, 97);
        width: 60rem;
        height: 2rem;
        background-color: rgb(85, 84, 84);
        display: flex;
        align-items: center;
        border-top-left-radius: 5px;
        border-top-right-radius: 5px;
    }

    .btns{
        width: 20px;
        height: 20px;
        border-radius: 50%;
        cursor: pointer;
        margin-left: 10px;
    }
    .close{
        background: rgb(255, 0, 0);
    }
    .close:hover{
        background: rgb(214, 1, 1);
    }
    .minimize{
        background-color: rgb(255, 187, 0);
    }
    .minimize:hover{
        background-color: rgb(226, 166, 1); 
    }
    .maximize{
        background-color: rgb(99, 205, 50);
    }
    .maximize:hover{
        background-color: rgb(87, 179, 44);
    }
    .inputDiv{
        display: flex;
        align-items: center;
        justify-content: center;
        margin-top: 15px;
        margin-bottom: 15px;
    }
    .input{
        width: 40rem;
        height: 2rem;
        border: 1px solid rgb(202, 201, 201);
        border-radius: 4px;
        outline: none;
    }
    .addBtn{
        height: 2rem;
        width: 2rem;
        background-color: rgb(99, 99, 255);
        border: none;
        outline: none;
        border-radius: 50%;
        color: white;
        cursor: pointer;
        margin-left: 10px;
    }
    .addBtn:hover{
        background-color: rgb(85, 85, 223);
    }

    .outputDiv{
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        min-height: 40rem;
        flex-direction: column;
    }

    .output{
        border: 1px solid rgb(199, 199, 199);
        border-radius: 5px;
        min-height: 39rem;
        width: 95%;
        display: flex;
        flex-direction: column;
        background-color: rgb(226, 226, 226);
    }
    .toDo{
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        font-family: 'Poppins', sans-serif;
        background: linear-gradient(rgb(218, 218, 218), rgb(211, 211, 211));
    }
    
    .checkMark{
        width: 1.5rem;
        margin-right: 10px;
        cursor: pointer;
    }

    .toDoItem{
        margin-left: 10px;
        font-size: 1rem;
    }
    .completeBtn{
        font-family: 'Poppins', sans-serif;
        font-size: 1rem;
        margin: 10px;
        background-color: rgb(99, 99, 255);
        color: white;
        border: none;
        outline: none;
        border-radius: 4px;
        padding: 7px;
        cursor: pointer;
    }
    .completeBtn:hover{
        background-color: rgb(85, 85, 223);
    }

</style>