<script>
    import { productPkg } from "../Stores/ProductStore"
    import { User } from "../Stores/UserStore"
    import { navigate } from "svelte-routing"
    import { beforeUpdate } from "svelte"
    import prodImg1 from "../assets/imagen1.jpg"
    import prodImg2 from "../assets/imagen2.jpg"
    import prodImg3 from "../assets/imagen3.jpg"
    import prodImg4 from "../assets/imagen4.jpg"
    import prodImg5 from "../assets/imagen5.jpg"
    import prodImg6 from "../assets/imagen6.jpg"
    import prodImg7 from "../assets/imagen7.jpg"
    import prodImg8 from "../assets/imagen8.jpg"
    import prodImg9 from "../assets/imagen9.jpg"
    import Offsale from "../assets/OffLogo.svg"
    
    export let ItemsClass
    export let discount
    export let itemSelected
    const products = []

    let modernMaleOut = new ItemsClass ("Modern Outfit Male", prodImg1, 55, "M", [])
    let summerWomenOut = new ItemsClass ("Summer Outfit Women", prodImg6, 29.99, "S")
    let ofWhite = new ItemsClass ("OfWhite Headsets", prodImg4, 25, "Universal")
    let casualOut = new ItemsClass ("Casual Outfit for Men", prodImg3, 49.99, "L")
    let sportOut = new ItemsClass ("Sporty outfit with accessories", prodImg2, 35, "L  and M")
    let grungeOut = new ItemsClass ("Grunge Outfit For Girl", prodImg5, 20, "S, L  and M",)
    let beachAcc = new ItemsClass ("Beach accessories for women", prodImg7, 19.99, "Universal")
    let girlSport = new ItemsClass ("Sporty Oufit for Women", prodImg8, 29.99, "S")
    let chicOut = new ItemsClass ("Fall outfit for a girl", prodImg9, 49.99, "S")

    products.push(modernMaleOut, summerWomenOut, casualOut, ofWhite, sportOut, grungeOut, beachAcc, girlSport, chicOut)

    function displayLargeView(item) {
        itemSelected = [item]
        navigate("/Product", {replace: true, preserveScroll: true})
    }

    beforeUpdate(() => {
        discount(products)
    })
</script>

<section class="basis-[80%] relative bg-transparent w-[60%] h-auto p-4 border-r border-b rounded-md lg:mb-60 lg:w-[80%] transition-all drop-shadow-lg shadow-lg">
    <h2 class="text-lg mb-2">Our Products:</h2>
    <div class="HomeDivSet">
    {#each products as prod }
        <figure class="HomefigSet group" on:dblclick={() => {displayLargeView(prod)}}>
            <img class="HomeImgSet" src={prod.photo} loading="lazy" alt="">
            <button on:click={() => productPkg.add(prod)}  class="absolute z-10 top-3 left-3 flex justify-center items-center w-10 h-10 p-1 bg-slate-200/50 border rounded-2xl active:bg-slate-500/50 transition duration-150 peer">
                <img class="w-[90%] h-[90%]" src={$productPkg.includes(prod) ? prod.favIcon : prod.unFavIcon} alt="">
            </button>
            <figure class="HomeHiddenFlag">
                <img class={$User ? 'globalImgRules' : 'hidden'} src={Offsale} alt="">
            </figure>
            <div class="HomeHiddenInfo group-hover:opacity-100">
                <h2 class="text-base">{prod.name}</h2>
                <p class="text-sm">Size: {prod.size}</p>
            {#if $User}
                <div class="flex gap-x-2 lg:gap-x-4">
                    <h3 class="text-base line-through whitespace-nowrap lg:text-lg">Before ${prod.price}</h3>
                    <h3 class="text-base lg:text-lg whitespace-nowrap text-red-500/85">Now ${prod.discountedPrice}</h3>
                </div>
            {:else}
                <div>
                    <h3 class="text-base whitespace-nowrap lg:text-lg">Price ${prod.price}</h3>
                </div>
            {/if}
            </div>
        </figure>
    {/each}
    </div>
</section>


