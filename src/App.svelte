<script>
  import Carousel from "svelte-carousel";
  const images = [
    {
      url: "https://p4.wallpaperbetter.com/wallpaper/403/494/469/interior-interior-design-indoors-wallpaper-preview.jpg",
      description: "image1",
    },
    {
      url: "https://p4.wallpaperbetter.com/wallpaper/860/803/694/interior-design-style-design-home-wallpaper-preview.jpg",
      description: "image2",
    },
    {
      url: "https://p4.wallpaperbetter.com/wallpaper/304/52/890/room-design-style-interior-wallpaper-preview.jpg",
      description: "image3",
    },
    {
      url: "https://p4.wallpaperbetter.com/wallpaper/472/430/507/living-style-furniture-design-wallpaper-preview.jpg",
      description: "image4",
    },
    {
      url: "https://p4.wallpaperbetter.com/wallpaper/290/818/435/interior-room-style-design-wallpaper-preview.jpg",
      description: "image5",
    },
  ];
  let carousel; // for calling methods of the carousel instance
  const handleNextClick = () => {
    carousel.goToNext();
  };

  let text = "Hello, Svelte!";

  // 시차 효과 스크립트 시작
  import { Parallax, ParallaxLayer} from 'svelte-parallax'
	
  
	let parallax;
	let disabled = window.matchMedia("(prefers-reduced-motion: reduce)").matches;
	
	const url = (name, wrap = false) => `${wrap ? 'url(' : ''}https://awv3node-homepage.surge.sh/build/assets/${name}.svg${wrap ? ')' : ''}`
  // 시차 효과 스크립트 종료

  // 줌 페이드 효과 스크립트 시작
  let y = 0
	let innerHeight

	function calculate(y, startY, endY, startValue, endValue) {
		const diffY = endY - startY
		const diffValue = endValue - startValue

		if (y < startY) {
			return startValue
		} else if(startY <= y && y <= endY) {
			const progress = (y - startY)/diffY
			return startValue + (diffValue * progress)
		} else if(endY < y){
			return endValue
		}
	}

	import { fade } from 'svelte/transition';
  // 줌 페이드 효과 스크립트 종료
</script>

<style>
  .container {
    position: relative;
    /* width: 300px;
    height: 200px; */
  }

  .img-container {
    /* width: 100%;
    height: 100%; */
    opacity: 0.4; /* 투명도  */
    width: 100%; /* 모바일 웹 및 데스크탑 웹을 위해 가로 사이즈 풀 */
    height: 700px; /* 모바일 웹 화면을 위해 높이 700px 로 고정 */
    background-position: -50px -30px; /* 원하는 부분의 위치 */
    object-fit: cover; /* 이미지를 비율 유지하며 가득 채움 */
    transition: background-color 0.3s ease;
  }

  .overlay-appbar-left {
    position: absolute;
    top: 5%;
    left: 10%;
    transform: translate(-50%, -50%);
    font-size: 20px;
    color: white;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  }

  .overlay-appbar-right {
    position: absolute;
    top: 5%;
    right: 0%;
    transform: translate(-50%, -50%);
    font-size: 20px;
    color: white;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  }

  /* 시차 효과 스타일 */
  :global(body) {
		padding: 0;
	}
	.server, .bash, .clients-main {
		cursor: pointer;
	}
	img:focus {
		outline: 1px dotted gray;
	}
	img:focus:not(:focus-visible) {
		outline: none;
	}
	.server:focus-visible {
		outline: 2px dotted gray;
	}
	.bash:focus-visible {
		outline: 2px dotted purple;
	}
	.clients-main:focus-visible {
		outline: 2px dotted blue;
	}
</style>

<div class="drawer drawer-end">
  <input id="my-drawer-3" type="checkbox" class="drawer-toggle" /> 
  
  <div class="drawer-content flex flex-col">
    <!-- Navbar start -->
    <nav class="sticky top-0">
      
    </nav>
    <div class="overlay-appbar-left">
      <div class="w-full navbar ">
        <div class="flex-1 px-2 mx-2 table-pin-rows">꾸민</div>
        <div class="flex-none hidden lg:block">
          <ul class="menu menu-horizontal">
            <!-- Navbar menu content here -->
            <li><a>홈</a></li>
            <li><a>로그인</a></li>
          </ul>
        </div>
      </div>
    </div>
    <!-- Navbar end -->
    <Carousel
      bind:this={carousel}
      let:loaded
      autoplay
      autoplayDuration={3000}
      autoplayProgressVisible={false}
      arrows={false}
      swiping={true}
    >
    {#each images as src, imageIndex (src)}
      <div class="container">
        {#if loaded.includes(imageIndex)}
          <img 
            src={src.url} 
            alt={src.description} 
            class=img-container  
          />
          <div>{text}</div>
        {/if}
      </div>
    {/each}
  </Carousel>

    <div class="overlay-appbar-right">
      <div class="flex-none lg:hidden">
        <label for="my-drawer-3" class="btn btn-square btn-ghost">
          <svg 
            xmlns="http://www.w3.org/2000/svg" 
            fill="none" 
            viewBox="0 0 24 24" 
            class="inline-block w-6 h-6 stroke-current"
          >
            <path 
              stroke-linecap="round" 
              stroke-linejoin="round" 
              stroke-width="2" 
              d="M4 6h16M4 12h16M4 18h16"
            >
            </path>
          </svg>
        </label>
      </div>
    </div>
    <!-- Page content here -->
    
  </div> 
  
  <div class="drawer-side">
    <label for="my-drawer-3" class="drawer-overlay"></label> 
    <ul class="menu w-full h-full bg-gray-100 text-gray-500">
      <!-- Navbar -->
      <nav class="sticky top-0">
        <div class="w-full navbar text-gray-600">
          <div class="flex-1 px-2 mx-2 table-pin-rows">꾸민</div>
          <div class="flex-none hidden lg:block">
            <ul class="menu menu-horizontal">
              <!-- Navbar menu content here -->
              <li><a>홈</a></li>
              <li><a>로그인</a></li>
            </ul>
          </div>
          <div class="flex-none lg:hidden">
            <label 
              for="my-drawer-3" 
              class="btn btn-square btn-ghost"
            >
              <!-- svg 속성 -->
              <svg 
                xmlns="http://www.w3.org/2000/svg" 
                fill="none" 
                viewBox="0 0 24 24" 
                class="inline-block w-6 h-6 stroke-current">
                <path 
                  stroke-linecap="round" 
                  stroke-linejoin="round" 
                  stroke-width="2" 
                  d="M6 18L18 6M6 6l12 12"
                ></path>
              </svg>
            </label>
          </div>
        </div>
      </nav>
      <!-- Sidebar content here -->
      <li><a>홈</a></li>
      <li><a>항목</a></li>
    </ul>
  </div>
</div>

<!-- 시차 효과 -->
<Parallax 
  sections=3
  style="background-color: #253237;" {disabled} 
  bind:this={parallax}
>
		<ParallaxLayer 
      offset=1 
      rate=1 
      style="background-color: #FFE5CC;" 
    />
		<ParallaxLayer 
      offset=2 
      rate=1 
      style="background-color: #87BCDE;" 
    />
		<ParallaxLayer 
      offset=0 
      rate=0 
      span=3 
      style="background-image: { url('stars', true) }; background-size: cover;"
    />
	
		<ParallaxLayer 
      offset=1.3  
      rate=-0.3
    >
			<img 
        src={url('satellite4')} 
        alt='' 
        style="width: 15%; margin-left: 70%;"
      >
		</ParallaxLayer>
		
		<ParallaxLayer 
      offset=1 
      rate=0.8 
      style="opacity: 0.1;"
    >
			<img 
        src={url('cloud')} 
        alt='' 
        style="display: block; width: 20%; margin-left: 55%;"
      >
			<img 
        src={url('cloud')} 
        alt='' 
        style="display: block; width: 10%; margin-left: 15%;"
      >
		</ParallaxLayer>
		  
		<ParallaxLayer 
      offset=1.75 
      rate=0.5 
      style="opacity: 0.1;"
    >
			<img 
        src={url('cloud')} 
        alt='' 
        style="display: block; width: 20%; margin-left: 70%;"
      >
			<img 
        src={url('cloud')} 
        alt='' 
        style="display: block; width: 20%; margin-left: 40%;"
      >
		</ParallaxLayer>
		
		<ParallaxLayer 
      offset=1 
      rate=0.2 
      style="opacity: 0.2;"
    >
			<img 
        src={url('cloud')} 
        alt='' 
        style="display: block; width: 10%; margin-left: 10%;"
      >
			<img 
        src={url('cloud')} 
        alt='' 
        style="display: block; width: 20%; margin-left: 75%;"
      >
		</ParallaxLayer>

    <ParallaxLayer 
      offset=1.6
      rate=0.4
      style="opacity: 1.0;"
    >
    <center>또 다른 세계</center>
    <center>나의 비슷한 조건의 사용자들의</center>
    <center>리얼한 후기들을 확인하고</center>
    <center>내게 딱 맞는 파트너와 함께 해요!</center>
		</ParallaxLayer>
		 
		<ParallaxLayer 
      offset=1.3
      rate=-0.1 
      style="opacity: 0.4;"
    >
			<img 
        src={url('cloud')} 
        alt='' 
        style="display: block; width: 20%; margin-left: 60%;"
      >
			<img 
        src={url('cloud')} 
        alt='' 
        style="display: block; width: 25%; margin-left: 30%;"
      >
			<img 
        src={url('cloud')} 
        alt='' 
        style="display: block; width: 10%; margin-left: 80%;"
      >
		</ParallaxLayer>
		
		<ParallaxLayer 
      offset=2.6 
      rate=0.4 
      style="opacity: 0.6;"
    >
			<img 
        src={url('cloud')} 
        alt='' 
        style="display: block; width: 20%; margin-left: 5%;"
      >
			<img 
        src={url('cloud')} 
        alt='' 
        style="display: block; width: 15%; margin-left: 75%;"
      >
		</ParallaxLayer>
		
		<ParallaxLayer 
      offset=2.5 
      rate=-0.4 
      style="display: flex; align-items: center; justify-content: center;"
    >
			<img 
        src={url('earth')} 
        alt='' 
        style="width: 60%;"
      >
		</ParallaxLayer>

		<ParallaxLayer 
		  offset=2
			rate=-0.3
			style="display: flex; align-items: center; justify-content: center;"
		>
			<img 
        src={url('clients')} 
        alt='' 
        style="height: 80%; width: 80%;"
      >
	</ParallaxLayer>

		<ParallaxLayer 
		  offset=0 
			rate=0.1
			style="display: flex; align-items: center; justify-content: center;"
		>
			<img 
			  src={url('server')} 
			  alt='' 
				class="server" 
				style="width: 20%;" 
				on:click={() => parallax.scrollTo(2, {selector: '.bash'})}
			  on:keyup={(e) => e.key === 'Enter' && parallax.scrollTo(2, {selector: '.bash'})}
		    tabindex=0
			>
		</ParallaxLayer>
		<ParallaxLayer 
		  offset=1
			rate=0.1
			style="display: flex; align-items: center; justify-content: center;"
		>
			<img 
			  src={url('bash')} 
				alt=''
				class="bash"
				style="width: 40%;"  
				on:click={() => parallax.scrollTo(3, {selector: '.clients-main'})}
			  on:keyup={(e) => e.key === 'Enter' && parallax.scrollTo(3, {selector: '.clients-main'})} 
			  tabindex=0
			>
		</ParallaxLayer>
		
		<ParallaxLayer 
		  offset=2
			rate=-0
			style="display: flex; align-items: center; justify-content: center;"
		>
			<img 
			  src={url('clients-main')} 
				alt='' 
				class="clients-main" 
				style="width: 40%;" 
				on:click={
          () => parallax.scrollTo(
            1, {
              selector: '.server'
            }
          )
        }
			  on:keyup={
          (e) => e.key === 'Enter' && parallax.scrollTo(
            1, {
              selector: '.server'
            }
          )
        }
			  tabindex=0
      >
		</ParallaxLayer>
	</Parallax>