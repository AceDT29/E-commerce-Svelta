<script>
  import { tags } from "../Imports/images";
  import { navigate } from "svelte-routing";

  const navTo = (tag) => {
    navigate(`/Search/${tag}`, {replace: true, preserveScroll: true})
  }
  
</script>

<div class="LoginSecForm  w-full flex-row justify-center gap-7 flex-wrap  mx-auto my-2">
  <button 
    on:click={() => navTo("Fit")}
    class="group CategoriesCont"
    >
    <figure class="w-full h-full group-hover:scale-110 transition duration-300">
      <img class="globalImgRules" src={tags.fitTag} alt="" />
    </figure>
    <div
      class="CategoriesHiddenInfo">
      <p class="text-lg text-slate-200 lg:text-2xl">Fit</p>
    </div>
  </button>
  <button
    on:click={() => navTo("Casual")}
    class="group CategoriesCont"
    >
    <figure class="w-full h-full group-hover:scale-110 transition duration-300">
      <img class="globalImgRules" src={tags.casualTag} alt="" />
    </figure>
    <div
      class="CategoriesHiddenInfo">
      <p class="text-lg text-slate-200 lg:text-2xl">Casual</p>
    </div>
  </button>
  <button
    on:click={() => navTo("Summer")}
    class="group CategoriesCont"
    >
    <figure class="w-full h-full group-hover:scale-110 transition duration-300">
      <img class="globalImgRules" src={tags.summerTag} alt="" />
    </figure>
    <div
      class="CategoriesHiddenInfo">
      <p class="text-lg text-slate-800 lg:text-2xl">Summer</p>
    </div>
  </button>
</div>
