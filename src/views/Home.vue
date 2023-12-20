<script setup></script>

<template>
  <div class="flex flex-col items-center">
    <div
      class="hero min-h-screen"
      style="
        background-image: url(https://www.pokepedia.fr/images/thumb/8/88/Volucit%C3%A9.png/800px-Volucit%C3%A9.png?20110301031940);
      "
    >
      <div class="hero-overlay bg-opacity-60"></div>
      <div class="hero-content text-center text-neutral-content">
        <div class="max-w-md">
          <h1 class="mb-5 text-5xl font-bold">Hello</h1>
          <p class="mb-5">Welcome to my Pokemon Site</p>
          <router-link :to="{ name: 'pokedex' }">
            <button class="btn btn-primary">Get Started</button>
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>
