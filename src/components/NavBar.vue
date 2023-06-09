<template>

  <div v-if="$route.path !== '/login'" class="p-4 space-y-4 md:px-32" style="top: 0; left: 0; position: sticky; background: #26a9e0;">

    <div class="flex justify-between items-center">
      <div class="flex items-center space-x-2">
        <img src="../assets/menu.svg" alt="" width="35">
        <img src="../assets/logotype.png" class="rounded-md" alt="KITOB.tj" width="50">
      </div>

      <div class="hidden lg:flex justify-center items-stretch space-x-2 mx-8" style="flex: 1">
        <button class="flex items-center space-x-2 bg-blue-800 rounded-xl p-2 text-white font-semibold">
          <img src="../assets/category.svg" alt="" width="30">          
          <span>Каталог</span>
        </button>
        <div class="flex items-center items-stretch" style="flex: 1">
          <input style="min-width: 500px; flex: 1;" class="bg-white outline-none rounded-lg rounded-r-none p-2 text-lg w-full" type="text" placeholder="Искать книгу">
          <img src="../assets/search.svg" alt="" width="35" class="bg-blue-800 rounded-lg px-2 rounded-l-none">
        </div>
      </div>

      <div class="flex items-center space-x-4">
        <img src="../assets/user.svg" alt="" width="30" @click="goToProfile">
        <img src="../assets/bookmark.svg" alt="" width="30" @click="navigateTo('/saved')">
        <div class="flex items-stretch">
          <img src="../assets/shopping-bag.svg" alt="" width="30" @click="navigateTo('/shopping')">
          <div class="rounded-full bg-red-800 px-2" style="position: relative; top: -17px; left: -13px">
            <span class="text-white text-xs font-bold">{{ $store.state.cartBooks.length }}</span>
          </div>
        </div>

      </div>
    </div>
     
    <div class="lg:hidden flex justify-center items-stretch space-x-2">

      <button class="hidden sm:flex items-center space-x-2 bg-blue-800 rounded-xl p-2 text-white font-semibold">
          <img class="hidden sm:block" src="../assets/category.svg" alt="" width="30">          
          <span>Каталог</span>
      </button>

      <div class="flex items-center items-stretch" style="flex: 1">
        <img src="../assets/search_black.svg" alt="" width="35" class="bg-white rounded-lg px-2 rounded-r-none">
        <input style="flex: 1" class="bg-white outline-none rounded-lg rounded-l-none p-2 text-lg" type="text" placeholder="Искать книгу">
      </div>
    </div>

    <div class="cats flex items-center text-white space-x-4 overflow-x-scroll scrollCont">
      <h1 class="text-lg ">Художественные</h1>
      <h1 class="text-lg ">Научные</h1>
      <h1 class="text-lg ">Саморазвитие</h1>
      <h1 class="text-lg ">Детские</h1>
    </div>

  </div>


</template>

<script>


export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    handleScroll() {
      
      if(window.scrollY == 0) {
        if(document.querySelector('.cats') !== null) {
          document.querySelector('.cats').style.display = 'flex'
        }
      } else {
        if(document.querySelector('.cats') !== null) {
          document.querySelector('.cats').style.display = 'none'
        }
      }
    },
    navigateTo(path) {
      this.$router.push(path)
    },
    goToProfile() {
      if(localStorage.kitobtj == undefined) {
        this.navigateTo('/login')
      } else {
        this.navigateTo('/profile')
      }
    }
  },
  created () {
    window.addEventListener('scroll', this.handleScroll);
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.scrollCont::-webkit-scrollbar {
  display: none;
}
</style>
