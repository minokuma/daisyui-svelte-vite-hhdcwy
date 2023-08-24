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
  let isDrawerOpen = false;
</script>

<style>
  .navbar {
    /* position: relative; */
    background-color: transparent;
    z-index: 1;
    pointer-events: auto; /* 클릭 가능하도록 설정 */
  }

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
    top: 35%;
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

<div class="h-screen w-full flex flex-col">
  <div class="drawer drawer-end">

  <input id="my-drawer-3" type="checkbox" class="drawer-toggle" /> 
    <div class="drawer-content flex flex-col">
      <!-- Navbar -->
      <div class="w-full navbar bg-base-300 sticky top-0">
        <div class="flex-1 px-2 mx-2">꾸민</div>
        <div class="flex-none hidden lg:block">
          <ul class="menu menu-horizontal">
            <!-- Navbar menu content here -->
            <li><a>홈</a></li>
            <li><a>로그인</a></li>
          </ul>
        </div>
        <div class="flex-none lg:hidden ">
          <label for="my-drawer-3" class="btn btn-square btn-ghost">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" class="inline-block w-6 h-6 stroke-current"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path></svg>
          </label>
        </div> 
      </div>

      <Carousel
        bind:this={carousel}
        let:loaded
        autoplay
        autoplayDuration={3000}
        autoplayProgressVisible={false}
        arrows={false}
        swiping={true}
        dots={false}
        particlesToShow={1}
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
      <!-- Page content here -->
    </div> 
  
    <!-- 드로어 사이드 -->
    <div class="drawer-side">
      <label for="my-drawer-3" class="drawer-overlay"></label> 
      <ul class="menu px-3 w-full h-full bg-base-200">
        <!-- Sidebar content here -->
        <!-- Navbar -->
      <div class="w-full navbar">
        <div class="flex-1 ">꾸민</div>
        <div class="flex-none hidden lg:block">
          <ul class="menu menu-horizontal">
            <!-- Navbar menu content here -->
            <li><a>홈</a></li>
            <li><a>로그인</a></li>
          </ul>
        </div>
        <div class="flex-none lg:hidden ">
          <label for="my-drawer-3" class="btn btn-square btn-ghost">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" class="inline-block w-6 h-6 stroke-current"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
          </label>
        </div> 
      </div>
        <br/>
        <li><a>홈</a></li>
        <li><a>로그인</a></li>
      </ul>
      
    </div>
  </div>
</div>
