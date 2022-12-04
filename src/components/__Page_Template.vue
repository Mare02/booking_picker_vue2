
<!--druge komponente stranice - primera radi ova komponenta predstavlja stranicu-->

<template>
  <div class=" w-full flex flex-col items-center mt-28 sm:mt-44">
    <div class="flex flex-wrap items-center w-full justify-center gap-7 p-2 max-sm:px-4 sm:p-4">
      <div v-for="home in HomesData" :key="home.id" class="flex flex-col w-full sm:w-auto font-semibold 
                                                            shadow-lg rounded-2xl sm:shadow-none">
        <div class="relative w-full h-96 sm:h-64 sm:w-64 xl:h-72 xl:w-72 shadow rounded-2xl overflow-hidden transition-all">
          <img class="h-full w-full object-cover" :src="home.image_url" alt="">
          <svg class="absolute top-4 right-4 invert" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="30" height="30" viewBox="0 0 256 256" xml:space="preserve">
            <defs>
            </defs>
            <g style="stroke: none; stroke-width: 0; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: none; fill-rule: nonzero; opacity: 1;" transform="translate(1.4065934065934016 1.4065934065934016) scale(2.81 2.81)" >
              <path d="M 64.44 12.016 c 5.225 0 10.136 2.035 13.831 5.729 c 7.626 7.626 7.626 20.035 0 27.662 l -19.44 19.44 L 45 78.677 L 31.169 64.846 l -19.44 -19.44 c -7.626 -7.626 -7.626 -20.035 0 -27.662 c 3.694 -3.694 8.606 -5.729 13.831 -5.729 c 5.225 0 10.136 2.035 13.831 5.729 l 1.367 1.367 L 45 23.354 l 4.242 -4.242 l 1.367 -1.367 C 54.304 14.05 59.216 12.016 64.44 12.016 M 64.44 6.016 c -6.541 0 -13.083 2.495 -18.073 7.486 L 45 14.869 l 0 0 l 0 0 l -1.367 -1.367 C 38.642 8.511 32.101 6.016 25.56 6.016 S 12.477 8.511 7.486 13.502 c -9.982 9.982 -9.982 26.165 0 36.147 l 19.44 19.44 c 0 0 0 0 0.001 0 L 45 87.163 l 18.073 -18.073 c 0 0 0 0 0 0 l 19.44 -19.44 c 9.982 -9.982 9.982 -26.165 0 -36.147 C 77.523 8.511 70.982 6.016 64.44 6.016 L 64.44 6.016 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: rgb(0,0,0); fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round" />
            </g>
          </svg>
        </div>
        <div class="flex flex-col items-start text-base p-4 sm:p-0">
          <span class="font-bold text-lg">{{home.location}}</span>
          <span>Added 3 weeks ago</span>
          <span>Jan 11-19</span>
          <div class="flex items-center gap-1 px-2 py-1 border-[0.13rem] border-gray-300 rounded-md">
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
  components:{
  },
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