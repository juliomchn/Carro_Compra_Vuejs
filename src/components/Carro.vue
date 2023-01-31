<template>
    <div>
        <ul class="list-group">
            <li class="list-group-item" v-for="item in items" :key="item.id"> 
                {{item.titulo}} - {{item.precio}}
                <button class="btn btn-danger float-right" @click="removeItem(item)"> Delete</button>
            </li>
        </ul>
        <div class="card p-3 my-5">
            <h4 class="text-center"> Total: $ {{ total }}</h4>
        </div>
    </div>    
</template>

<script>
export default {
    name: 'Carro',
    props: ['items'],
    computed:{
        total(){
            return this.items.reduce((acumulado, item) => acumulado + Number(item.precio), 0);
        }
    },
    methods:{
        removeItem(item){
            this.$emit('removeItem', item);
        }
    }
}
</script>