<script>
  import SideNav from "./lib/SideBar.svelte"
  import Banner from "./lib/Banner.svelte"
  import HomeSec from "./lib/Home.svelte"

  function enableMode() {
    document.body.classList.toggle("darkMode")
  }

</script>

<body class="">
  <main>
    <header class="mb-14 p-0">
      <Banner />
    </header>
    <article class="flex md:gap-8 lg:gap-x-16">
      <SideNav on:ChangeMode={enableMode}/>
      <HomeSec />
    </article>
    <footer class="w-full h-[60vh] border drop-shadow-2xl p-10">
        <div class="flex flex-col items-center gap-3">
          <h1 class="font-extrabold text-4xl">SS Modernity</h1>
          <p class="text-sm">Your way, your style</p>
        </div>   
    </footer>
  </main> 
</body>

 


