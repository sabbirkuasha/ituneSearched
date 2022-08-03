<script>
    import {page} from '$app/stores'
    import {onMount} from 'svelte'


    let songResults = []
    onMount( async()=>{
        const searched = $page.params.trackId
        console.log("specific song id is:" + searched)

        const ituneSearhedResult = await fetch(`https://itunes.apple.com/search?term=${searched}&entity=song`) 

        const res = await ituneSearhedResult.json( )

        songResults = res.results
        console.log(songResults)
        console.log(songResults.artistId)
    })
</script>



<section>
    This is the song id: {$page.params.trackId}
    <hr>
    {#each songResults as songResult}
        {songResult.artistName}
    {/each}
</section>
