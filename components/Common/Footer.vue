<template>
  <footer class="pt-30 pb-30">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <div class="text-center">
            <p class="fz-13">
              © 2023 Hawke is Proudly Powered by <span class="underline main-color"><a :href="data.author_link"
                  target="_blank"> {{ data.theme_author }}</a></span>
            </p>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>
  
<script setup>
//= Static Data
import data from '@/data/app.json';
</script>