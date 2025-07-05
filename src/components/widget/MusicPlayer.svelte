<script lang="ts">
  import { onMount } from 'svelte';

  export let src = '/Assets/song.mp3';
  export let cover = '/Assets/cover.jpg';
  export let title = '歌曲标题';
  export let artist = '歌手名称';

  let audioEl: HTMLAudioElement;
  let playing = false;

  function togglePlay() {
    if (!audioEl) return;
    playing ? audioEl.pause() : audioEl.play();
    playing = !playing;
  }

  onMount(() => {
    audioEl.addEventListener('ended', () => (playing = false));
  });
</script>

<div
  class="group relative w-full aspect-square rounded-xl overflow-hidden shadow-lg cursor-pointer"
  on:click={togglePlay}
  style="background: url({cover}) center/cover no-repeat;"
>
  <audio bind:this={audioEl} src={src} preload="auto" class="hidden" id="myAudio" />

  <!-- 毛玻璃遮罩 -->
  <div
    class="absolute inset-0 bg-black/25 backdrop-blur-md flex flex-col items-center justify-center
           opacity-0 group-hover:opacity-100 transition-opacity duration-200"
  >
    <!-- Apple Music 风格圆形按钮 -->
    <div class="relative">
      <div
        class="w-16 h-16 bg-white/70 rounded-full shadow-[0_4px_14px_rgba(0,0,0,0.3)]
               flex items-center justify-center transform transition-all duration-200
               group-hover:scale-110" id="playPauseBtn"
      >
          <svg viewBox="0 0 24 24" fill="currentColor" class="w-7 h-7 text-gray-900" id="play-btn" hidden>
            <rect x="6" y="5" width="4" height="14" rx="1" />
            <rect x="14" y="5" width="4" height="14" rx="1" />
          </svg>
          <svg viewBox="0 0 24 24" fill="currentColor" class="w-7 h-7 text-gray-900" id="pause-btn" display="block">
            <path d="M8 5v14l11-7z" />
          </svg>
      </div>
    </div>

    <!-- 歌曲信息 -->
    <div class="mt-4 text-center text-white">
      <div class="font-semibold text-lg">{title}</div>
      <div class="text-sm mt-1">{artist}</div>
    </div>
  </div>
</div>

