<template>
    <div class="product-list">
        <ul>
            <li v-for="item in items" :key="item.id">
                <img v-bind:src="item.image_link" alt="{{ item.name }}" />
                <p>{{ item.name }}</p>
                <p>{{ item.price }}</p>
            </li>
        </ul>
    </div>
</template>

<script>
    import axios from 'axios';
    export default {
        data() {
            return {
                items: []
            };
        },
        mounted() {
            this.fetchItems();
        },
        methods: {
            fetchItems() {
                axios.get('http://makeup-api.herokuapp.com/api/v1/products.json?brand=maybelline').then((response)=> {
                    console.log('yellow', response.data)
                    this.items = response.data
                }).catch((error)=> {
                    console.log(error)
                })
            }
        }
    }
</script>


