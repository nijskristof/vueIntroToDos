<template>
    <div>
        <form @submit="addToDo">
            <input type="text" v-model="title" name="title" placeholder='Add Todo'>
            <input type="submit" value="Submit" class="btn" /> 
        </form>
    </div>
</template>

<script>
import uuid from 'uuid';
export default {
    name: 'AddToDo' ,
    methods:{
        addToDo(e){
            e.preventDefault();
            if(this.title === ""){
                return;
            }
            const newToDo={
                id: uuid.v4(),
                title: this.title,
                completed: false
            }
            this.$emit('add-todo', newToDo);
        }
    },
    data(){
        return{
            title:""
            }
    }
}
</script>

<style scoped>
    form{
        display:flex;
    }
    input[type="text"]{
        flex:10;
        padding:5px;
    }
    input[type="submit"]{
        flex:2;
    }
</style>
