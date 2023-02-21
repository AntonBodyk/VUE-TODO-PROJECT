<template>
    <header class="header">
      <div class="container">
        <div class="logo">ToDo List</div>
            <form class="form" @submit.prevent="addTask">
                <input
                    type="text"
                    v-model="task.inputValue"
                    v-on:keypress.enter="addTask"
                    required
                    > 
                <button class="btn" type="submit">Add a new task</button>
            </form>
      </div>
    </header>
</template>
 
<script>
    export default {
        data() {
            return{
                task: {
                    inputValue: ''
                }
            }
        },
        methods: {
            addTask() {
                this.task.id = Date.now();
                this.$emit('create', this.task);
                this.task = {
                    inputValue: ''
            }
        }
    }
}
</script>
 
<style scoped>
    .header {
        background-color: #333;
        padding: 10px 0;
        margin: -10px 0 40px -10px;
    }
    .header .container {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .header .container .logo {
        width: 200px;
        line-height: 50px;
        color: #ddd;
        font-size: 24px;
        cursor: pointer;
    }
    .header .container .form {
        width: 60%;
        display: flex;
        justify-content: space-between;
    }
    .header .container .form input {
        width: calc(100% - 145px);
        height: 40px;
        text-indent: 10px;
        border: 1px solid #fff;
        border-radius: 5px;
        border-radius: 0;
        box-sizing: border-box;
        outline: none;
        transition: 0.2s border;
    }
    .header .container .form input:focus {
        border: 1px solid #12c0dd;
    }
    .btn {
        background-color: #12c0dd;
        border: 1px solid #12c0dd;
        color: #fff;
        font-weight: 700;
        text-transform: uppercase;
        padding: 10px 15px;
        font-size: 12px;
        height: 40px;
        outline: none;
        transition: 0.2s;
    }
    .btn:hover {
        background-color: #0dd6f8;
        border-color: #0dd6f8;
    }
</style>