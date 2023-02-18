<template>
    <div class="container">
        <h2>
            <span>Done</span>
            <span class="mask-num">0</span>
        </h2>
        <ul class="mask-list complete-list">
            <li>
            <div>
                <input type="checkbox" checked>
                <span>Сходить в магазин</span>
            </div>
            <button class="btn-remove">Remove</button>
            </li>
        </ul>
    </div>
</template>
 
<script>
    export default {
        data() {
            return{}
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
        border: 2px solid #2a2f36;
        color: #2a2f36;
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
</style>