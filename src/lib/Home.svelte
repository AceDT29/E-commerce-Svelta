<script>
    import { productPkg } from "../Stores/ProductStore"
    import { User } from "../Stores/UserStore"
    import { navigate } from "svelte-routing"
    import { createEventDispatcher, onMount } from "svelte"
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
    import fav from "../assets/FavouriteIcon.svg"
    import notFav from "../assets/NotFavouriteIcon.svg"
    
    export let ItemsClass
    const products = []
    const dispatch = createEventDispatcher()

    let modernMaleOut = new ItemsClass ("Modern Outfit Male", prodImg1, 55, "M",)
    let summerWomenOut = new ItemsClass ("Summer Outfit Women", prodImg6, 29.99, "S",)
    let ofWhite = new ItemsClass ("OfWhite Headsets", prodImg4, 25, "Universal",)
    let casualOut = new ItemsClass ("Casual Outfit for Men", prodImg3, 49.99, "L",)
    let sportOut = new ItemsClass ("Sporty outfit with accessories", prodImg2, 35, "L  and M",)
    let grungeOut = new ItemsClass ("Grunge Outfit For Girl", prodImg5, 20, "S, L  and M",)
    let beachAcc = new ItemsClass ("Beach accessories for women", prodImg7, 19.99, "Universal")
    let girlSport = new ItemsClass ("Sporty Oufit for Women", prodImg8, 29.99, "S")
    let chicOut = new ItemsClass ("Fall outfit for a girl", prodImg9, 49.99, "S")

    products.push(modernMaleOut, summerWomenOut, casualOut, ofWhite, sportOut, grungeOut, beachAcc, girlSport, chicOut)

    function prodSelec(prodItem) {
        if ($User) {
            ItemsClass.setProductDiscount(prodItem)
        }
        productPkg.add(prodItem)
    }

    function displayLargeView(item) {
        let itemSelected = item
        dispatch("Send", [itemSelected])
        navigate("/Product", {replace: true, preserveScroll: true})
    }

    function discountedStateChecker(item){
        if($User) {
            item.forEach((obj) => {
                ItemsClass.setProductDiscount(obj)
            })
            return
        }
    }

    onMount(() => {
        discountedStateChecker(products)
    })

</script>

<section class="basis-[80%] relative bg-transparent w-[60%] h-auto p-4 border-r border-b rounded-md lg:mb-60 lg:w-[80%] transition-all drop-shadow-lg shadow-lg">
    <h2 class="text-lg mb-2">Our Products:</h2>
    <div class="HomeDivSet">
    {#each products as prod }
        <figure class="HomefigSet group" on:dblclick={() => {displayLargeView(prod)}}>
            <img class="HomeImgSet" src={prod.photo} alt="">
            <button on:click={() => prodSelec(prod)}  class="absolute z-10 top-3 left-3 flex justify-center items-center w-10 h-10 p-1 bg-slate-200/50 border rounded-2xl active:bg-slate-500/50 transition duration-150 peer">
                <img class="w-[90%] h-[90%]" src={$productPkg.includes(prod) ? fav : notFav} alt="">
            </button>
        {#if $User}
            <figure class="absolute w-12 h-12 top-0 left-[77%] hover:scale-110 transition-all lg:w-16 lg:h-16 lg:left-[78%]">
                <img class="block w-full h-full" src={Offsale} alt="">
            </figure>
        {/if}
            <div class="HomeHiddenInfo group-hover:opacity-100">
                <h2 class="text-base">{prod.name}</h2>
                <p class="text-sm">Size: {prod.size}</p>
                <h3 class="text-lg">Price: {$User ? prod.discountedPrice : prod.price}$</h3>
            </div>
        </figure>
    {/each}
    </div>
</section>


