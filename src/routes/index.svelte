<script>
    import {goto} from '$app/navigation'

    let searchedValue
    const search = ()=> {
        // this is static way to change route
        // goto('search/searchedResult')

        // this is dynamic way to change route 
        goto(`${searchedValue}`)

        console.log(searchedValue)
    }
</script>

<section>
    <div class="m-auto text-center p-5">
        <div>
            <h1 class="p-5 text-3xl">Search an artist</h1>
        </div>
        <input  class="input input-bordered input-secondary" 
                type="text"
                bind:value={searchedValue}>
        <button class="btn btn-secondary"
                on:click={search}>
            Search Now 
        </button>
    </div>
</section>