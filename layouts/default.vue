<template>
  <div id='main-wrapper' class='fixed top-0 bottom-0 right-0 left-0 flex items-stretch'>
    
    <div id='main-contanier' class='flex-auto flex items-stretch'>
      <div id='side-bar' class='bg-black flex flex-column justify-center items-center'>
        <div class='flex flex-column gray-2'>
          <div class='mb4'>
            <div class='triangle'></div>
          </div>
          <div class='mb4'>
            <div class="circle bg-gray-2"></div>
          </div>
          <div>
            <div class='sqaure bg-gray-3'></div>
          </div>
        </div>
      </div>
      <div id='page-area'>
        <nuxt />
      </div>
    </div>
    
  </div>
</template>

<style src='../static/app.css'>

</style>
