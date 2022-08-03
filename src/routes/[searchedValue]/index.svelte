<script>
    import {page} from '$app/stores'
    import {goto} from '$app/navigation'

    import {onMount} from 'svelte'
    import SongList from '$lib/SongList.svelte'

    let songResults = []
    onMount( async()=>{
        const searched = $page.params.searchedValue

        const ituneSearhedResult = await fetch(`https://itunes.apple.com/search?term=${searched}&entity=song`) 

        const res = await ituneSearhedResult.json( )

        songResults = res.results
        console.log(songResults)
    })
</script>

<section>
    <!-- <div>
        {$page.params.searchedValue}
    </div> -->
    <div class="p-4">

    </div>

    <div class="mb-2 flex flex-row flex-wrap w-screen gap-10 justify-center">
        {#each songResults as singleSong}
            <SongList   songTitle={singleSong.collectionCensoredName}
                        trackName = {singleSong.trackName}
                        songArtist={singleSong.artistName}
                        songID={singleSong.artistId}
                        songArtwork = {singleSong.artworkUrl100}
                        songPrice = {singleSong.collectionPrice}
                        songURL ={$page.params.searchedValue+'/'+ singleSong.trackId}
                        />
            <!-- <button class="btn btn-primary"
                    on:click={goto(`${$page.params.searchedValue}/${singleSong.trackId}`)}>
                Go to Song
            </button> -->
        {/each}
    </div>
    
    
    
    
    

</section>