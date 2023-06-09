<template>
    
    <div class="lg:px-64 py-4 lg:py-16 px-4 space-y-8">
        <div class="flex justify-between items-center my-2">
            <div class="space-y-2">
                <h1 class="text-start text-xl font-bold">Салом, {{ username }} !</h1>
                <h1 class="text-start text-md text-gray-600">{{ tel }}</h1>  
                <h1 class="text-start text-md text-gray-600">{{ email }}</h1>                
            </div>

            <img src="../assets/user-octagon.svg" alt="" width="60">
        </div>

        <h1 class="text-start text-xl font-bold">Заказы</h1>
        <div class="p-4 shadow-xl">
            
            <div v-for="book in info" class="cursor-pointer my-8 flex items-stretch border-b-2 space-x-4 pb-8" @click="$router.push('/book/' + book.id)">
                    <img :src="book.cover" alt="" width="100">
                    <div>
                        <h1 class="text-start text-md font-bold">{{ book.name }}</h1>
                        <h1 class="text-start text-sm">{{ book.author }}</h1>
                        <h1 :class="['text-start text-lg font-bold mt-8',getStatusColor(book.status)]">{{ book.status }}</h1>
                        <h1 class="text-start text-md text-blue-600 mt-8">{{ book.date }}</h1>

                    </div>

            </div>

        </div>

    </div>


</template>

<script>
    export default {
        data: () => ({
            username: JSON.parse(localStorage.kitobtj).username,
            tel: JSON.parse(localStorage.kitobtj).tel,
            email: JSON.parse(localStorage.kitobtj).email,
            info: [
                {
                id: 3,
                name: 'Думай и богатей',
                author: "Наполеон Хилл",
                cover: 'https://bookhouse.kg/media/galleryphoto/2022/5/bd0e464c-39cb-4fad-b49f-80f65fe2f14d.webp.360x460_q94.jpg',
                status: 'Принят',
                date: '23.05.2023'
                }
        ]
        }),
        methods: {
            getStatusColor(status) {
                if(status == 'Принят') {
                    return 'text-green-700'
                } else if(status == 'На рассмотрении') {
                    return 'text-blue-600'
                } else {
                    return 'text-red-800'
                }

            }
        },
        computed: {
            // getStatusColor(status) {
            //     if(status == 'Принят') {
            //         return 'text-green-700'
            //     }


            // }
        }
    }
</script>










