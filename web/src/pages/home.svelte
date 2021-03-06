<script lang="ts">
  import Button from '../components/Button.svelte';
  import CreatorCard from '../components/CreatorCard.svelte';
  import {creators} from '../stores/queries';
  import SignUp from '../components/SignUp.svelte';
  import About from '../components/About.svelte';
  import {quintOut} from 'svelte/easing';
  import {fade, draw, fly} from 'svelte/transition';
  import {expand} from '../utils/custom-transitions.js';
  import {onMount} from 'svelte';
  import 'pathseg';

  import Particles from 'svelte-particles';

  let visible = false;

  const inner = `M99.95 1.57L2.05 1.57L2.05 99.48L99.95 99.48L84.49 83.65L17.51 83.65L17.51 17.4L84.49 17.4L99.95 1.57Z`;
  const outer = `M31.33 64.18L56 77.86L80.68 64.18L80.68 36.83L56 23.16L31.33 36.83L31.33 64.18Z`;

  let particlesConfig = {
    detectRetina: false,
    fpsLimit: 60,
    interactivity: {
      detectsOn: 'canvas',
      events: {
        onHover: {
          enable: true,
          mode: 'bubble',
        },
        resize: true,
      },
      modes: {
        bubble: {
          distance: 60,
          duration: 10,
          opacity: 1,
          size: 10,
        },
      },
    },
    particles: {
      color: {
        value: '#30DAAC',
      },
      links: {
        blink: false,
        color: '#18CFCD',
        consent: false,
        distance: 50,
        enable: true,
        opacity: 0.9,
        width: 2.5,
      },
      move: {
        attract: {
          enable: false,
          rotate: {
            x: 300,
            y: 600,
          },
        },
        bounce: false,
        direction: 'none',
        enable: true,
        outMode: 'bounce',
        random: true,
        speed: 0.7,
        straight: false,
      },
      number: {
        density: {
          enable: false,
          area: 1000,
        },
        limit: 0,
        value: 300,
      },
      opacity: {
        animation: {
          enable: false,
          minimumValue: 0.05,
          speed: 2,
          sync: false,
        },
        random: false,
        value: 0.5,
      },
      shape: {
        type: 'circle',
      },
      size: {
        animation: {
          enable: false,
          minimumValue: 0.5,
          speed: 20,
          sync: true,
        },
        random: true,
        value: 1,
      },
    },
    polygon: {
      draw: {
        enable: true,
        lineColor: 'rgba(0,255,255,0.2)',
        lineWidth: 0.5,
      },
      move: {
        radius: 7,
      },
      position: {
        x: 20,
        y: 15,
      },
      inlineArrangement: 'equidistant',
      scale: 5,
      type: 'inline',
      data: `<svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" style="isolation:isolate" viewBox="0 0 636 636" xml:space="preserve"><defs><clipPath id="_clipPath_ufUKWNh03Q0ow8cg9bS2G9dNbT4C2wP3"><rect width="636" height="636"/></clipPath></defs><g><path d="M99.95 1.57L2.05 1.57L2.05 99.48L99.95 99.48L84.49 83.65L17.51 83.65L17.51 17.4L84.49 17.4L99.95 1.57Z M31.33 64.18L56 77.86L80.68 64.18L80.68 36.83L56 23.16L31.33 36.83L31.33 64.18Z M31.33 64.18L80.68 64.18L56 23.16 Z M31.33 36.83L80.68 36.83L56 77.86 Z M56 23.16L 56 77.86 M 31.33 64.18L80.68 36.83 M31.33 36.83L80.68 64.18 M99.95 1.57L17.51 17.4 M2.05 1.57L84.49 17.4 M17.51 83.65L2.05 99.48L84.49 83.65 M2.05 1.57L17.51 17.4 M17.51 83.65L99.95 99.48 M17.51 17.4L2.05 20.36L17.51 83.65L2.05 80.69L17.51 17.4"/></g></svg>`,
    },
  };

  onMount(() => {
    visible = true;
  });

  let onParticlesLoaded = (event) => {
    const particlesContainer = event.detail.particles;
    particlesContainer.play();
    // you can use particlesContainer to call all the Container class
    // (from the core library) methods like play, pause, refresh, start, stop
  };

  const name = 'Creators spotlight';

  creators.fetch();
</script>

<div class="bg-indigo-600">
  <div class="max-w-7xl mx-auto py-3 px-3 sm:px-6 lg:px-8">
    <div class="flex items-center justify-between flex-wrap">
      <div class="w-0 flex-1 flex items-center">
        <span class="flex p-2 rounded-lg bg-indigo-800">
          <!-- Heroicon name: speakerphone -->
          <svg
            class="h-6 w-6 text-white"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            aria-hidden="true">
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M11 5.882V19.24a1.76 1.76 0 01-3.417.592l-2.147-6.15M18 13a3 3 0 100-6M5.436 13.683A4.001 4.001 0 017 6h1.832c4.1 0 7.625-1.234 9.168-3v14c-1.543-1.766-5.067-3-9.168-3H7a3.988 3.988 0 01-1.564-.317z" />
          </svg>
        </span>
        <p class="ml-3 font-medium text-white truncate">
          <span class="md:hidden"> We won the ETHOnline Textile hackathon prize! </span>
          <span class="hidden md:inline"> Big news! We won the ETHOnline Textile hackathon prize! </span>
        </p>
      </div>
      <div class="order-3 mt-2 flex-shrink-0 sm:order-2 sm:mt-0 sm:w-auto">
        <a
          href="https://blog.textile.io/creaton-ethonline-winner/"
          class="flex items-center justify-center px-4 py-2 border border-transparent rounded-md shadow-sm text-sm font-medium text-indigo-600 bg-white hover:bg-indigo-50">
          Blog post
        </a>
      </div>
      <div class="order-2 flex-shrink-0 sm:order-3 sm:ml-3 hidden">
        <button
          type="button"
          class="-mr-1 flex p-2 rounded-md hover:bg-indigo-500 focus:outline-none focus:ring-2 focus:ring-white sm:-mr-2">
          <span class="sr-only">Dismiss</span>
          <!-- Heroicon name: x -->
          <svg
            class="h-6 w-6 text-red"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>
    </div>
  </div>
</div>

<div>
  <main>
    <!--<Particles class="hidden" options={particlesConfig} on:particlesLoaded={onParticlesLoaded} />-->
    <div class="relative pt-16 pb-32 flex content-center items-center justify-center min-h-screen-75">
      <div
        class="absolute top-0 w-full h-full bg-center bg-cover"
        style="
          background-image: url(https://ipfs.rarible.com/ipfs/QmUPQQC2G5mwjZV22K5Nv1Y5ARad4jgR8cv2UEK4Ltx3Cq/image.gif);
        ">
        <span id="blackOverlay" class="w-full h-full absolute opacity-75 bg-black" />
      </div>
      <div class="container relative mx-auto">
        <div class="items-center flex flex-wrap">
          <div class="w-full lg:w-8/12 px-4 ml-auto mr-auto text-center">
            <div class="relative pr-0 w-2/5 ml-auto mr-auto">
              {#if visible}
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 103 124">
                  <g out:fade={{duration: 200}} opacity="1">
                    <path in:expand={{duration: 400, delay: 1000, easing: quintOut}} style="fill: #43e296;" d={outer} />
                    <path
                      in:draw={{duration: 2000}}
                      style="stroke:#000000; stroke-width: 1.5; fill: #43e296;"
                      d={inner} />
                  </g>
                </svg>
                <div
                  class="-mt-8 lg:-mt-20 text-4xl lg:text-8xl text-green-400 text-center"
                  out:fly={{y: -20, duration: 800}}>
                  {#each 'Creaton' as char, i}<span in:fade={{delay: 1000 + i * 15, duration: 800}}>{char}</span>{/each}
                </div>
                <div class="mt-8 mb-6 text-sm lg:text-xl text-gray-300" out:fly={{y: -20, duration: 800}}>
                  {#each 'Decentralized Content Sharing Platform' as char, i}
                    <span in:fade={{delay: 1000 + i * 15, duration: 800}}>{char}</span>
                  {/each}
                </div>
              {/if}
            </div>
          </div>
        </div>
      </div>
      <div
        class="top-auto bottom-0 left-0 right-0 w-full absolute pointer-events-none overflow-hidden h-70-px"
        style="transform: translateZ(0);">
        <svg
          class="absolute bottom-0 overflow-hidden"
          xmlns="http://www.w3.org/2000/svg"
          preserveAspectRatio="none"
          version="1.1"
          viewBox="0 0 2560 100"
          x="0"
          y="0">
          <polygon class="text-gray-300 fill-current" points="2560 0 2560 100 0 100" />
        </svg>
      </div>
    </div>

    <section class="pb-20 bg-gradient-to-b from-green-300 via-indigo-200 to-yellow-100 -mt-24">
      <div class="container mx-auto px-4">
        <div class="flex flex-wrap">
          <div class="lg:pt-12 pt-6 w-full md:w-4/12 px-4 text-center md:mt-16">
            <div
              class="relative flex flex-col min-w-0 break-words bg-white w-full mb-8 shadow-lg rounded-l-3xl border-indigo-500 border-2">
              <div class="px-4 py-5 flex-auto">
                <div
                  class="text-white p-3 text-center inline-flex items-center justify-center w-12 h-12 mb-5 shadow-lg rounded-full bg-red-400">
                  <i class="fas fa-play" />
                </div>
                <h6 class="text-xl font-semibold">Support Creators</h6>
                <p class="mt-2 mb-4 text-gray-600">
                  Get exclusive content from creators through a stablecoin streaming subscription
                </p>
              </div>
            </div>
          </div>

          <div class="w-full md:w-4/12 px-4 text-center">
            <div
              class="relative flex flex-col min-w-0 break-words bg-white w-full mb-8 shadow-lg rounded-t-3xl border-indigo-500 border-2">
              <div class="px-4 py-5 flex-auto">
                <div
                  class="text-white p-3 text-center inline-flex items-center justify-center w-12 h-12 mb-5 shadow-lg rounded-full bg-green-400">
                  <i class="fas fa-dollar-sign" />
                </div>
                <h6 class="text-xl font-semibold">Fund Your Creating</h6>
                <p class="mt-2 mb-4 text-gray-600">
                  Earn money by creating content for subscribers, with investors betting on your farming reward success
                </p>
              </div>
            </div>
            <div
              class="relative flex flex-col min-w-0 break-words bg-white w-full mb-8 shadow-lg rounded-b-3xl border-indigo-500 border-2">
              <div class="px-4 py-5 flex-auto">
                <div
                  class="text-white p-3 text-center inline-flex items-center justify-center w-12 h-12 mb-5 shadow-lg rounded-full bg-green-400">
                  <i class="fas fa-tractor" />
                </div>
                <h6 class="text-xl font-semibold">Farm CREATE</h6>
                <p class="mt-2 mb-4 text-gray-600">Earn rewards for farming CREATE token, our burning utility token</p>
              </div>
            </div>
          </div>

          <div class="pt-6 w-full md:w-4/12 px-4 text-center md:mt-16">
            <div
              class="relative flex flex-col min-w-0 break-words bg-white w-full mb-8 shadow-lg rounded-r-3xl border-indigo-500 border-2">
              <div class="px-4 py-5 flex-auto">
                <div
                  class="text-white p-3 text-center inline-flex items-center justify-center w-12 h-12 mb-5 shadow-lg rounded-full bg-blue-400">
                  <i class="fas fa-hands-helping" />
                </div>
                <h6 class="text-xl font-semibold">Farm Creatonks</h6>
                <p class="mt-2 mb-4 text-gray-600">
                  Kickstart creator careers by buying Creatonks (creator tokens), receive rewards for farming
                </p>
              </div>
            </div>
          </div>
        </div>

        <div class="container mx-auto px-4 w-full md:w-10/12">
          <div class="items-center flex flex-wrap">
            <div class="w-full md:w-4/12 ml-auto mr-auto px-4" />
            <img alt="..." src="https://i.imgur.com/IM7pQmM.jpg" class="w-full align-middle rounded-lg" />
          </div>
        </div>
      </div>
    </section>
    <About />
  </main>
</div>

<section class="py-8 px-4 text-center bg-gradient-to-b from-teal-100 to-white">
  <div class="w-fill mx-auto mt-4 mb-10">
    <h1 class="text-indigo-600 font-bold text-6xl mb-10 font-heading">{name}</h1>
  </div>
  <div class="py-4">
    <div class="mx-auto px-4 sm:px-6 lg:max-w-screen-xl lg:px-8">
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
        {#if !$creators.state}
          <div>creators not loaded</div>
        {:else if $creators.error}
          <div>Error: {$creators.error}</div>
        {:else if $creators.state === 'Fetching'}
          <div>Loading creators...</div>
        {:else}
          {#each $creators.data as creator, index}
            <CreatorCard {creator}>{creator.creatorContract}</CreatorCard>
          {/each}
        {/if}
      </div>
    </div>
  </div>
</section>

<section class="pt-20">
  <div class="container px-4 mx-auto w-5/6 lg:w-3/6 mb-24">
    <h2 class="text-5xl font-semibold text-center">Technologies</h2>
    <div class="grid grid-flow-row-dense grid-cols-3 grid-rows-2 gap-4 lg:gap-20 items-center align-middle">
      <img alt="..." src="/images/nucypher.png" />
      <img alt="..." src="/images/ethereum.png" />
      <img alt="..." src="/images/filecoin.png" />
      <img alt="..." src="/images/superfluid.png" />
      <img alt="..." src="/images/textile.png" />
    </div>
    <div class="container mx-auto px-4">
      <div class="flex flex-wrap text-center">
        <div class="w-full px-4">
          <h4 class="text-3xl font-semibold">Keep updated on our progress!</h4>
          <SignUp />
          <h5 class="text-lg mt-0 mb-2 text-gray-700">Find us on any of these platforms.</h5>
          <div class="mt-6 lg:mb-0 mb-6">
            <a
              class="hover:text-gray-600 text-gray-800 px-3 py-2 items-center justify-center align-center text-xs uppercase font-bold"
              href="https://twitter.com/creaton_io"
              target="_blank">
              <i class="text-gray-500 fab fa-twitter text-lg leading-lg" />
            </a>
            <a
              class="hover:text-gray-600 text-gray-800 px-3 py-2 items-center justify-center align-center text-xs uppercase font-bold"
              href="https://github.com/creaton-io/creaton?ref=homepage"
              target="_blank">
              <i class="text-gray-500 fab fa-github text-lg leading-lg" />
            </a>
            <a
              class="hover:text-gray-600 text-gray-800 px-3 py-2 items-center justify-center align-center text-xs uppercase font-bold"
              href="https://medium.com/creaton"
              target="_blank">
              <i class="text-gray-500 fab fa-medium-m text-lg leading-lg" />
            </a>
            <a
              class="hover:text-gray-600 text-gray-800 px-3 py-2 items-center justify-center align-center text-xs uppercase font-bold"
              href="https://creaton.on.fleek.co"
              target="_blank">
              <i class="text-gray-500 fab fa-telegram-plane text-lg leading-lg" />
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
