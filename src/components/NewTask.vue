<template>
    <div class="container">
      <h2>
        <span>To Do</span>
        <span class="mask-num">{{ newtasks.length }}</span>
      </h2>
      <ul class="mask-list">
        <li v-for="task of newtasks" :key="task.id">
          <div>
            <input type="checkbox" v-on:change="newChacked(index, 'new')"/>
            <span>{{task.inputValue}}</span>
          </div>
          <button class="btn-remove" @click="$emit('remove', task)">Remove</button>
        </li>
      </ul>
    </div>
</template>
 
<script>
    export default {
        props: {
            newtasks: {
                type: Array,
                required: true
            },
            completedtasks: {
                type: Array,
                required: true
            }     
        },
        methods: {
            newChacked(index, type) {
                if(type === 'new') {
                    const checkedTask = this.newtasks.splice(index, 1);
                    this.completedtasks.push(...checkedTask);
                }
            }
        }
    }
</script>
 
<style scoped>
    h2 {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding-bottom: 20px;
        margin: 25px 0;
        border-bottom: 1px solid #bfbfbf;
    }

    h2 .mask-num {
        border-radius: 20px;
        border: 2px solid red;
        color: red;
        font-size: 14px;
        font-weight: 700;
        padding: 5px 10px;
    }

    .mask-list li {
        display: flex;
        align-items: center;
        justify-content: space-between;
        height: 32px;
        line-height: 32px;
        margin-bottom: 10px;
        border-radius: 3px;
        background-color: #fff;
        }

    .mask-list.complete-list li {
        border-left-color: #999;
        opacity: .5;
    }
    .mask-list {
        padding-left: 0;
    }

    input[type="checkbox"] + span {
        padding-left: 10px;
    }

.btn-remove {
    border: 1px solid #2a2f36;
    font-size: 12px;
    border: 2px solid #2a2f36;
    background-color: #333333;
    color: #fff;
    font-weight: 700;
    text-transform: uppercase;
    padding: 5px 10px;
    font-size: 12px;
    outline: none;
    transition: 0.2s;
}

.btn-remove:hover {
  background-color: #535151;
  border-color: #535151;
}

input[type="checkbox"]:checked,
input[type="checkbox"]:not(:checked){
   position: absolute;
   z-index: 1;
   opacity: 0;
   width: 20px;
   height: 20px;
   margin-top: 6px;
}

input[type="checkbox"]:checked + span,
input[type="checkbox"]:not(:checked) + span{
   position: relative;
   padding-left: 35px;
   cursor:pointer;
}
input[type="checkbox"]:checked + span::before{
   content:'';
   position: absolute;
   width: 16px;
   height: 16px;
   left:0;
   top:calc(50% - 10px);
   background-color: transparent;
   border-radius: 2px;
   border: 2px solid #4fc1de;
}
input[type="checkbox"]:checked + span::after{
   content:'';
   position: absolute;
   width: 12px;
   height: 12px;
   transition: all .2s ease;
   opacity: 1;
   left: 4px;
   top: calc(50% - 6px);
   background-color: #4fc1de;
}
input[type="checkbox"]:not(:checked) + span::before{
   content:'';
   position: absolute;
   width: 16px;
   height: 16px;
   left:0;
   top:calc(50% - 10px);
   background-color: transparent;
   border-radius: 2px;
   border: 2px solid #5d575f;
}
input[type="checkbox"]:not(:checked) + span::after{
   content:'';
   position: absolute;
   width: 12px;
   height: 12px;
   transition: all .2s ease;
   opacity: 0;
   left: 4px;
   top: calc(50% - 6px);
   background-color: #7d25a9;
}
</style>