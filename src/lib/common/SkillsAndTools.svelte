<script lang='ts'>
  import { onMount } from "svelte";

  export let workItem: any;
  let image = '';
  onMount(async () => {
    image = (await import(`../../content/${workItem.icon}.svg`)).default;
  });
</script>
<div class="flex flex-col items-center justify-center gap-3 p-6">
  <div class="h-8 sm:h-10">
    <img
      alt={workItem.name}
      title={workItem.name}
      loading="lazy"
      width="40"
      height="40"
      decoding="async"
      class="h-full w-auto rounded-lg"
      src={image}
      style="color: transparent;"
    />
  </div>
  <p class="text-black text-sm">{workItem.name}</p>
</div>