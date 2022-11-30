/*druge komponente stranice - primera radi jedna komponenta predstavlja stranicu*/ 

<template>
  <div class=" w-full flex flex-col items-center h-screen mt-44">
    <div class="flex flex-wrap items-center w-full justify-center gap-7 p-2 sm:p-4">
      <div v-for="home in HomesData" :key="home.id" class="flex flex-col w-full sm:w-auto">
        <div class="w-full h-96 sm:h-64 sm:w-64 lg:h-72 lg:w-72 shadow rounded-2xl overflow-hidden transition-all">
          <img class="h-full w-full object-cover" :src="home.image_url" alt="">
        </div>
        <div class="flex flex-col items-start text-base">
          <span class="font-bold text-lg">{{home.location}}</span>
          <span>Added 3 weeks ago</span>
          <span>Jan 11-19</span>
          <div class="flex items-center gap-1">
            <span class="font-bold">${{home.price}}</span>
            <span>night</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      HomesData: [
        {
          id: 1,
          title: 'example apartment title',
          location: 'Location, Example',
          price: 100,
          image_url: 'https://images.unsplash.com/photo-1589129140837-67287c22521b?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8NXx8dmFjYXRpb24lMjBob21lfGVufDB8fDB8fA%3D%3D&auto=format&fit=crop&w=500&q=60'
        },
        {
          id: 2,
          title: 'example apartment title',
          location: 'Location, Example',
          price: 100,
          image_url: 'https://images.unsplash.com/photo-1605352081508-2e09927ecfe3?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8OXx8dmFjYXRpb24lMjBob21lfGVufDB8fDB8fA%3D%3D&auto=format&fit=crop&w=500&q=60'
        },
        {
          id: 3,
          title: 'example apartment title',
          location: 'Location, Example',
          price: 100,
          image_url: 'https://images.unsplash.com/photo-1608783550473-54d5b54a51af?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTF8fHZhY2F0aW9uJTIwaG9tZXxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=500&q=60'
        },
        {
          id: 4,
          title: 'example apartment title',
          location: 'Location, Example',
          price: 100,
          image_url: 'https://images.unsplash.com/photo-1499793983690-e29da59ef1c2?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTR8fHZhY2F0aW9uJTIwaG9tZXxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=500&q=60'
        },
        {
          id: 5,
          title: 'example apartment title',
          location: 'Location, Example',
          price: 100,
          image_url: 'https://images.unsplash.com/photo-1606030689001-3ee5ac74e3bf?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8Mjd8fHZhY2F0aW9uJTIwaG9tZXxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=500&q=60'
        },
        {
          id: 6,
          title: 'example apartment title',
          location: 'Location, Example',
          price: 100,
          image_url: 'https://images.unsplash.com/photo-1595483921906-7da233885832?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MzR8fHZhY2F0aW9uJTIwaG9tZXxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=500&q=60'
        },
        {
          id: 7,
          title: 'example apartment title',
          location: 'Location, Example',
          price: 100,
          image_url: 'https://images.unsplash.com/photo-1589129140837-67287c22521b?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8NXx8dmFjYXRpb24lMjBob21lfGVufDB8fDB8fA%3D%3D&auto=format&fit=crop&w=500&q=60'
        },
        {
          id: 8,
          title: 'example apartment title',
          location: 'Location, Example',
          price: 100,
          image_url: 'https://images.unsplash.com/photo-1605352081508-2e09927ecfe3?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8OXx8dmFjYXRpb24lMjBob21lfGVufDB8fDB8fA%3D%3D&auto=format&fit=crop&w=500&q=60'
        },
        {
          id: 9,
          title: 'example apartment title',
          location: 'Location, Example',
          price: 100,
          image_url: 'https://images.unsplash.com/photo-1608783550473-54d5b54a51af?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTF8fHZhY2F0aW9uJTIwaG9tZXxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=500&q=60'
        },
        {
          id: 10,
          title: 'example apartment title',
          location: 'Location, Example',
          price: 100,
          image_url: 'https://images.unsplash.com/photo-1499793983690-e29da59ef1c2?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTR8fHZhY2F0aW9uJTIwaG9tZXxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=500&q=60'
        },
        {
          id: 11,
          title: 'example apartment title',
          location: 'Location, Example',
          price: 100,
          image_url: 'https://images.unsplash.com/photo-1606030689001-3ee5ac74e3bf?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8Mjd8fHZhY2F0aW9uJTIwaG9tZXxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=500&q=60'
        },
        {
          id: 12,
          title: 'example apartment title',
          location: 'Location, Example',
          price: 100,
          image_url: 'https://images.unsplash.com/photo-1595483921906-7da233885832?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MzR8fHZhY2F0aW9uJTIwaG9tZXxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=500&q=60'
        },
      ]
    }
  }
}
</script>

<style>
</style>