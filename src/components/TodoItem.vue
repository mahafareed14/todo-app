<template>
    <div class="task">
        <p> {{item_name}}</p>
        <button @click="$emit('remove')"> X </button>
    </div>   
</template>
<script>
export default {
    name: 'TodoItem',
    props: {
        item_name: String
    },
}
</script>

<style lang="scss">
    .task {
        border: 5px solid #6ea4c8;
        border-radius: 10px;
        padding: 0px 25px;
        color: white;
        background: #6ea4c8;
        width:360px;
        margin-top: 5px;
        display: -webkit-inline-box;
        button {
            border-radius: 50%;
            background-color: #42a8ec;
            border: none;
            color: white;
            text-align: center;
            margin-left: 360px;
            margin-top: 17px;
            position: absolute;
            display: inline-block;
            font-size: 17px;
        }
    }
</style>