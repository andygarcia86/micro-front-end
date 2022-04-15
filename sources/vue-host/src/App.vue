<template>
<div class="mx-auto max-w-screen-xl">
  <div>
    user info
  </div>
  <div class="grid grid-cols-3 gap-4">
    <div>
      Menu
      <ul>
        <li>Vue module</li>
        <li>V2 module</li>
      </ul>
      <Search />  
      <br>
      What's In Your Growler
      <Cart />
    </div>
    <div class="col-span-2">
      <iframe src="https://localhost:44391/" title="V2 sample" width="100%" height="400"></iframe>

      <div class="m-3 text-xl">
        We also like <span class="font-bold">{{filteredTaps}}</span>
      </div>
      <Taps />
    </div>
  </div>  
</div>
</template>

<script lang="ts">
import { Component } from "Vue";
import Taps from 'growlers/Taps';
import Search from 'growlers/Search';
import Cart from 'growlers/Cart';
import store from 'growlers/store';

export default {
  components: {
    Search,
    Taps,
    Cart,
  },
  computed: {
    filteredTaps: {
      get() {
        return store.filteredTaps.slice(0, 3).map(({ beverageName }: { beverageName: string }) => beverageName).join(', ');
      },
      set() {
      }
    }
  }
}
</script>