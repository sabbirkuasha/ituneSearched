<!-- <script>
    import {page} from '$app/stores'
    import {onMount} from 'svelte'

    let songResult = []
    onMount( async()=>{
        const searched = $page.params.searchedValue
        const ituneSearhedResult = await fetch(`https://itunes.apple.com/search?term=${searched}&entity=song`) 
        const res = await ituneSearhedResult.json( )
        songResult = res.results
        console.log(songResult)
    })
</script>

<section>
    <div>
        {$page.params.searchedValue}
    </div>
</section> -->

