<script lang="ts">
  import { onMount } from "svelte";
  import { goto } from "$app/navigation";
  import work from "$lib/images/work.png";

  export let item: any;
  export let index: number;
  let image = "";
  let path =
    item.workImage && item.workImage !== ""
      ? ``
      : work;

  const handleImageLoadError = (ev: any) => (ev.target.src = work);

  const handleRouting = () => {
    goto(`/work/${index}`);
  };

  const handleKeyDown = (e: any) => {
    if ((e.code === "Enter")) {
      handleRouting();
    }
  };

  onMount(async () => {
    image = (await import(`../../content/${item.workImage}.png`)).default;
  });
</script>

<div
  class="relative shadow-lg rounded-lg cursor-pointer h-[100%] hover:scale-105 focus-visible:scale-105 transition-all ease-in-out group"
  on:click={handleRouting}
  on:keypress={handleKeyDown}
  role="button"
  tabindex=0
>
  <img
    src={image}
    alt={item.name}
    title={item.name}
    on:error={handleImageLoadError}
    class="rounded-lg w-[100%] h-[100%] object-cover"
  />
  <div class="opacity-0 group-focus-visible:opacity-100 group-hover:opacity-100 duration-300 absolute left-0 bottom-0 right-0 z-10 text-xl text-[#face55] flex flex-col justify-between font-semibold h-[100%] bg-black bg-opacity-60 text-center p-[2em] rounded-lg">
    <h3 class="text-2xl ">{item.name}</h3>
    <span class="text-sm p-[8px] max-w-[60%] mx-auto rounded-lg border border-[#face55] hover:text-black hover:bg-[#face55]">View this Project</span>
  </div>
</div>
