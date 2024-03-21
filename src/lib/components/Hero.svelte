<script lang="ts">
  import { onMount } from "svelte";
  import content from "../../content/content.json";
  let profile = "";
  let phraseList = ["Hello! I am","ನಮಸ್ಕಾರ! ನಾನು","हॅलो! हांव","नमस्ते! मैं हूँ", "హలో! నేను", "வணக்கம்! நான்", "नमस्कार! मी आहे", "Hola yo soy", "Ciao! Sono", "Bonjour! Je suis", "Hello! I am"]
  let phraseIndex = 0;
  onMount(async () => {
    typing();
    profile = (await import(`../../content/${content.profileImage}.jpg`)).default;
  });

  let phrase = phraseList[0]; // text to be typed
  let typedChar = ""; // SECTION displaying typed text
  let index = 0;
  let typewriter: number; // for setInterval/clearInterval

  // If Input is empty, clear out SECTION displaying typed text
  $: if (!phrase) {
    typedChar = "";
    index = typedChar.length;
  }

  let isTyping = false;

  const typeChar = () => {
    if (index < phrase.length) {
      isTyping = true;
      typedChar += phrase[index];
      index += 1;
    } else {
      index = 0;
      if(phraseIndex < phraseList.length -1){
        phraseIndex += 1;
        typedChar=""
      } else {
        stopTyping();
      }
      phrase=phraseList[phraseIndex]
      return;
    }
  };

  const typing = () => (typewriter = setInterval(typeChar, 250));

  const stopTyping = () => {
    clearInterval(typewriter);
    isTyping = false;
  };
</script>

<section
  class="relative text-center md:p-[7em] min-h-[100vh] flex flex-col justify-center"
>
  <div class="max-w-[1344px] mx-auto">
    <div
      style={`background-image: url('${profile}');`}
      class={`w-[275px] h-[275px] mx-auto mb-[48px] rounded-[50%]  bg-cover`}
    >
    </div>
    <div class="text-5xl">
      <p class="pr-[8px] md:inline min-h-[50px]">{typedChar}</p>
      <h1 class="font-semibold text-5xl leading-2 md:inline text-[#face55]">
        {content.name}
      </h1>
    </div>
    <article
      class="my-[24px] text-2xl max-w-[70%] md:max-w-[60%] text-center mx-auto"
    >
      {content.description}
    </article>
  </div>
  <div class="hidden lg:block absolute bottom-4 w-[25px] h-[40px] border-2 border-black rounded-[35%] left-[50%]">
    <span class="text-3xl leading-0 block animate-bounce duration-100">.</span>
  </div>
</section>
