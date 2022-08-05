<script>
    import {page} from '$app/stores'
    import {onMount} from 'svelte'
    import AudioPlayer from '$lib/AudioPlayer.svelte'


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



<section class="text-center">
    <div class="p-5">
        The song id: {$page.params.trackId}
    </div>
    

    {#each songResults as songResult}
        <div class=" flex flex-col justify-center">
            <img class="w-60 m-auto" src={songResult.artworkUrl100} alt={songResult.artistName}>
            <h1>{songResult.artistName}</h1>
            <div class="m-auto">
                <audio controls>
                    <source src={songResult.previewUrl} type="audio/ogg">
                </audio>
            </div>
            
        </div>
        
        <div class="flex flex-col w-full border-opacity-50">
            <div class="divider">OR</div>
        </div>

        <AudioPlayer    trackName = {songResult.trackCensoredName}
                        albumName = {songResult.collectionName}
                        artistName = {songResult.artistName} 
                        artworkurl = {songResult.artworkUrl100}
                        trackpreviewUrl = {songResult.previewUrl}              
        />
    {/each}

    
</section>
