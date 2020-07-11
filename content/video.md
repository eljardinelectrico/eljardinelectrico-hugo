+++
title = "Videos"
date = 2020-07-10T17:53:37+09:00
color = "#efce53"
+++

<div class="video-player">
  <div class="video-player__playing">
    <div class="embed-container">
      <div id="player"></div>
    </div>
  </div>
  <div class="video-player__thumbs">
    <div data-video="OfCHJQTjO3c" class="video-thumb active"><img src="https://img.youtube.com/vi/OfCHJQTjO3c/hqdefault.jpg"></div>
    <div data-video="8cHHUdf_oO4" class="video-thumb"><img src="https://img.youtube.com/vi/8cHHUdf_oO4/hqdefault.jpg"></div>
    <div data-video="fmNBdwNjw1Y" class="video-thumb"><img src="https://img.youtube.com/vi/fmNBdwNjw1Y/hqdefault.jpg"></div>
    <div data-video="M1nJ0YjSywk" class="video-thumb"><img src="https://img.youtube.com/vi/M1nJ0YjSywk/hqdefault.jpg"></div>
  </div>
</div>
<script>
function getChildren(n, skipMe){
    var r = [];
    for (; n; n = n.nextSibling) { 
       if (n.nodeType == 1 && n != skipMe) {
          r.push(n);        
      }
    }
    return r;
}
function getSiblings(n) {
    return getChildren(n.parentNode.firstChild, n);
}
const tag = document.createElement('script');
tag.src = "https://www.youtube.com/iframe_api";
const firstScriptTag = document.getElementsByTagName('script')[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);
let player;
function onYouTubeIframeAPIReady() {
  player = new YT.Player('player', {
    playerVars: {
        autoplay: 1,
        modestbranding: 1,
        rel: 0
    },
    height: '315',
    width: '560',
    videoId: 'OfCHJQTjO3c',
    events: {
      onReady: function() {
        document.querySelectorAll('.video-thumb').forEach(function(thumb) {
            console.log(thumb);
            thumb.onclick = function() {
                if (!thumb.classList.contains('active')) {
                    player.loadVideoById(thumb.getAttribute("data-video"));
                    thumb.classList.add('active');
                    getSiblings(thumb).forEach(function(sibling) {
                        sibling.classList.remove('active');
                    });
                }
            }
        });
      }
    }
  });
}
</script>
