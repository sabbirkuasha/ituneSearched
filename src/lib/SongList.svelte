<script>
  export let songTitle = 'Song Name'
  export let trackName = 'TrackName'
  export let songArtist = 'Song Artist'
  export let songID = 'Song ID'
  export let songPrice = 'Song Price'
  export let songArtwork = 'https://placeimg.com/400/225/arch'
  export let songURL = '/'
</script>


<div class="card card-side bg-slate-800 shadow-xl h-40 w-96">
  <a class="m-auto" href={songURL}>
    <figure class="p-3"><img src={songArtwork} alt={songArtist}></figure>
  </a>
  
  <div class="card-body p-3 bg-slate-700 ">
    <a href={songURL}>
      <h2 class="card-title">{trackName} - {songArtist}</h2>
    </a>
    <p class="">{songTitle}</p>
    <div class="card-actions justify-end">
      <div class="badge badge-primary">{songID}</div>
      <div class="badge badge-secondary">${songPrice}</div> 
      
    </div>
  </div>
</div>