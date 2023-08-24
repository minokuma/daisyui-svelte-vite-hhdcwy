<script>

 let isMobile = false;

  // 브라우저 창 크기에 따라 화면 크기를 판별하는 함수
  function checkWindowSize() {
    isMobile = window.innerWidth <= 640; // 기준 값 설정
  }

  // 초기화 시 화면 크기를 판별하고, 창 크기가 변경될 때마다 업데이트
  checkWindowSize();
  window.addEventListener('resize', checkWindowSize);


  import Carousel from "svelte-carousel";
  const images = [
    {
      url: "https://selinerapp.tk/images/wallpaper_1.jpg",
      description: "image1",
      text: "언제 어디서든<br/>꾸민하세요!"
    },
    {
      url: "https://selinerapp.tk/images/wallpaper_2.jpg",
      description: "image2",
      text: "새롭게 인테리어를<br/>꾸미고 싶을 때<br/>꾸민!"
    },
    {
      url: "https://selinerapp.tk/images/wallpaper_3.jpg",
      description: "image3",
      text: "새로운 분위기의<br/>전환이 필요할 때<br/>꾸민!"
    },
    {
      url: "https://selinerapp.tk/images/wallpaper_4.jpg",
      description: "image4",
      text: "내 마음대로<br/>꾸미고 싶을 때<br/>꾸민!"
    },
    {
      url: "https://selinerapp.tk/images/wallpaper_5.jpg",
      description: "image5",
      text: "순식간에<br/>디자인하고 싶을 때<br/>꾸민!"
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

  .overlay-appbar-center {
    position: absolute;
    top: 30%;
    /* left: 20%; */
    /* right: 50%; */
    /* transform: translate(-50%, -50%); */
    letter-spacing: 20;
    line-height: 1.4;
    font-weight: bold;
    color: white;
    /* text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5); */
  }

  .overlay-appbar-left {
    position: absolute;
    top: 60px;
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

  /* 줌 페이드 효과 시작 */
  #y-scroll {
		position: fixed;
		top: 1rem;
		left: 1rem;
		color: white;
		z-index: 10;
		font-size: 1.5rem;
		font-weight: bold;
	}
	#content {
		height: 500vh;
	}
	#home {
		height: 260vh;
		border-bottom: 5px solid #90aaa3;
	}
	#img-container {
		position: sticky;
		top: 0;
    width: 100%; /* 모바일 웹 및 데스크탑 웹을 위해 가로 사이즈 풀 */
    height: 750px; /* 모바일 웹 화면을 위해 높이 700px 로 고정 */
		/* width: 100%;
		height: 100vh; */
		background-image: url("https://selinerapp.tk/images/wallpaperbetter.com_2560x1440.jpg");
		background-position: 50% 50%;
		background-size: cover;
		background-repeat: no-repeat;		
	}
	h1 {
		color: white;
		text-align: center;
	}
	:global(body) {
		margin: 0;
		background-color: black;
	}
	:global(*){
		box-sizing: border-box;
	}
  /* 줌 페이드 효과 종료 */
</style>
<!-- Navbar start -->
<nav class="sticky top-0">
  <div class="overlay-appbar-left">
      <div class="w-full navbar ">
        <div class="flex-1 px-2 mx-2 table-pin-rows">꾸민 1</div>
        <div class="flex-none hidden lg:block">
          <ul class="menu menu-horizontal">
            <!-- Navbar menu content here -->
            <li><a>홈</a></li>
            <li><a>로그인</a></li>
          </ul>
        </div>
      </div>
    </div>
</nav>
<div class="drawer drawer-end">
  <input id="my-drawer-3" type="checkbox" class="drawer-toggle" /> 
  <div class="drawer-content flex flex-col">
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
          <div class="{isMobile ? 'inset-0 flex justify-center text-3xl' : 'mx-20 text-5xl' } overlay-appbar-center">
            {@html src.text}
          </div>
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


<svelte:window bind:scrollY={y} bind:innerHeight={innerHeight}/>

<!-- <div id="y-scroll">innerHeight(내부 높이) :  {innerHeight} - y {y}</div> -->
<!-- <div id="y-scroll">innerHeight(내부 높이) :  {innerHeight} - y {y}</div> -->

<div id="">
	<div id="">
		<!-- <div id="img-container"
			style:transform="scale({calculate(y, 0, 1*innerHeight, 1, 1.5)})"
			style:opacity="{calculate(y, 0.7 * innerHeight, 1.8 * innerHeight, 1, 0)}"
			>
		</div> -->
    <div id="img-container"
			style:opacity="{calculate(y + 700, 0.7 * innerHeight, 1.8 * innerHeight, 0, 1)}"
			>
		</div>
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
      style="background-color: #87deb9;" 
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
    <center text-black>또 다른 세계<br/>나의 비슷한 조건의 사용자들의<br/>리얼한 후기들을 확인하고<br/>내게 딱 맞는 파트너와 함께 해요!</center>

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

