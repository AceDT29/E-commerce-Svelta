<script>
  import { tags } from "../Imports/images.d";

  export let navTo;
  let isScrolling = false
  let targetScroll = 950

</script>

<div class="LoginSecForm  w-full flex-row justify-center gap-7 flex-wrap font-lobster mx-auto my-2">
  <button 
    on:click={() => navTo(targetScroll, isScrolling, "/Search/Fit")}
    class="group CategoriesCont"
    >
    <figure class="w-full h-full group-hover:scale-110 transition duration-300">
      <img class="globalImgs" src={tags.fitTag} alt="" />
    </figure>
    <div
      class="CategoriesHiddenInfo">
      <p class="text-lg text-slate-200 textShadow lg:text-2xl ">Fit</p>
    </div>
  </button>
  <button
    on:click={() => navTo(targetScroll, isScrolling, "/Search/Casual")}
    class="group CategoriesCont"
    >
    <figure class="w-full h-full group-hover:scale-110 transition duration-300">
      <img class="globalImgs" src={tags.casualTag} alt="" />
    </figure>
    <div
      class="CategoriesHiddenInfo">
      <p class="text-lg text-slate-200 textShadow lg:text-2xl ">Casual</p>
    </div>
  </button>
  <button
    on:click={() => navTo(targetScroll, isScrolling, "/Search/Summer")}
    class="group CategoriesCont"
    >
    <figure class="w-full h-full group-hover:scale-110 transition duration-300">
      <img class="globalImgs" src={tags.summerTag} alt="" />
    </figure>
    <div
      class="CategoriesHiddenInfo">
      <p class="text-lg text-slate-800 textShadow lg:text-2xl">Summer</p>
    </div>
  </button>
</div>
