<template>
  <div id='main-wrapper' class='fixed top-0 bottom-0 right-0 left-0 flex items-stretch'>
    
    <div id='main-contanier' class='flex-auto flex items-stretch'>
      <div id='side-bar' class='bg-black flex flex-column justify-center items-center'>
        <div class='flex flex-column gray-2'>
          <div class='mb5'>
            <nuxt-link to='/'><div class='triangle'></div></nuxt-link>
          </div>
          <div class='mb5'>
            <nuxt-link to='/work'><div class="circle bg-gray-2"></div></nuxt-link>
            
          </div>
          <div>
            <nuxt-link to='/about'><div class='sqaure bg-gray-3'></div></nuxt-link>
          </div>
        </div>
      </div>
      <div id='page-area' class='flex flex-auto items-stretch'>
        <nuxt />
      </div>
    </div>
    
  </div>
</template>

<style src='../static/app.css'>

</style>
