<script>


  import {
    Collapse,
    Navbar,
    Styles,
    NavbarToggler,
    NavbarBrand,
    Nav,
    NavItem,
    NavLink,
    Dropdown,
    DropdownToggle,
    DropdownMenu,
    DropdownItem,
    Button, 
    Icon
  } from 'sveltestrap';
	
  let theme = 'light';
  let isOpen = false;

  function handleUpdate(event) {
    isOpen = event.detail.isOpen;
  }
  
  import AiOutlineMenu from "svelte-icons-pack/ai/AiOutlineMenu";
  import AiOutlineClose from "svelte-icons-pack/ai/AiOutlineClose";

  
  // let isMenuOpen = false;

  // function toggleMenu() {
  //   alert();
  //   console.log('토글 메뉴!!');
  //   isMenuOpen = !isMenuOpen;
  // }


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

	import Sidebar from './Sidebar.svelte'
  
	import Main from './Main.svelte'

	let open = false
  import { reveal } from 'svelte-reveal';
  import Example1 from './reveal/Example1.svelte';

  // 메뉴
  function Menu(e) {
    // alert(e);
    let list = document.querySelector('ul');

    e.name === 'menu' 
      ? ( 
        e.name = "close", 
        list.classList.add('top-[80px]'), 
        list.classList.add('opacity-100')
      )
      : ( 
        e.name = "menu", 
        list.classList.remove('top-[80px'),
        list.classList.remove('opacity-100')
      )  
  }

  let menuState = "menu";

  // function toggleMenu() {
  //   let list = document.querySelector('ul');
    
  //   if (menuState === "menu") {
  //     menuState = "close";
  //     list.classList.add('top-[80px]');
  //     list.classList.add('opacity-100');
  //   } else {
  //     menuState = "menu";
  //     list.classList.remove('top-[80px]');
  //     list.classList.remove('opacity-100');
  //   }
  // }
  
  function toggleMenu(e) {
    menuState = menuState === "menu" ? "close" : "menu";
  }
  
</script>


<style>
  a { display: block; }

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


<Styles {theme} />


<Button
  color="primary"
  outline
  active={theme === 'light'}
  on:click={() => (theme = 'light')}
>
  라이트 <Icon name="sun-fill" />
</Button>
<Button
  color="primary"
  outline
  active={theme === 'dark'}
  on:click={() => (theme = 'dark')}
>
  다크 <Icon name="moon-stars-fill" />
</Button>
<Button
  color="primary"
  outline
  active={theme === 'auto'}
  on:click={() => (theme = 'auto')}
>
  기본 <Icon name="circle-half" />
</Button>

<nav class="... sticky top-0">
  <Navbar color="light" light expand="md" class="sticky top-0">
    <NavbarBrand href="/">
      <!-- 커서 포인터 영역 활성화 -->
        <span class="text-2xl font-[Poppins] cursor-pointer">
          <!-- 인라인 처리! -->
          <img class="h-8 inline" src="https://www.ggumin.me/images/logo-b.png" alt="">
          꾸민
        </span>
    </NavbarBrand>
    <NavbarToggler on:click={() => (isOpen = !isOpen)} />
    <Collapse {isOpen} navbar expand="md" on:update={handleUpdate}>
      <Nav class="ms-auto" navbar>
        <NavItem>
          <NavLink class="text-right" href="#">소개</NavLink>
        </NavItem>
        <NavItem>
          <NavLink class="text-right" href="#">채용</NavLink>
        </NavItem>
        <NavItem>
          <NavLink class="text-right" href="#">로그인</NavLink>
        </NavItem>
      </Nav>
    </Collapse>
  </Navbar>
</nav>


<!--  여기다 -->
<!-- <body class="bg-cyan-400">
  <nav class="p-5 bg-white shadow md:flex md:items-center md:justify-between">
    <div class="flex justify-between items-center">
      <span class="text-2xl font-[Poppins] cursor-pointer">
        <img class="h-8 inline" src="https://www.ggumin.me/images/logo-b.png" alt="">
        꾸민
      </span>

      <span class="text-3xl cursor-pointer mx-2 md:hidden block">
      
        <button on:click={toggleMenu}>{menuState}</button>

        <header class="drawer-content flex flex-col">
          <nav class="flex">
            {#if menuState === "menu"}
              <Icon src={AiOutlineMenu} on:click={toggleMenu} />
              <div>
                <a href="/">메뉴1</a>
                <a href="/">메뉴2</a>
                <a href="/">메뉴3</a>
                <a href="/">메뉴4</a>
            </div>
            {:else}
              <Icon src={AiOutlineClose} on:click={toggleMenu} />
            {/if}
          </nav>
        </header>
      </span>
    </div>
    <ul class="md:flex md:items-center z-[-1] md:z-auto md:static absolute bg-white w-full left-0 md:w-auto md:py-0 py-4 md:pl-0 pl-7">
      <li class="mx-4 my-6 md:my-0">
        <a href="#" class="text-xl hover:text-cyan-500 duration-500">HOME</a>
      </li>
      <li class="mx-4 my-6 md:my-0">
        <a href="#" class="text-xl hover:text-cyan-500 duration-500">SERVICE</a>
      </li>
      <li class="mx-4 my-6 md:my-0">
        <a href="#" class="text-xl hover:text-cyan-500 duration-500">ABOUT</a>
      </li>
      <li class="mx-4 my-6 md:my-0">
        <a href="#" class="text-xl hover:text-cyan-500 duration-500">CONTACT</a>
      </li>
      <li class="mx-4 my-6 md:my-0">
        <a href="#" class="text-xl hover:text-cyan-500 duration-500">LOGIN</a>
      </li>

      <button class="bg-cyan-400 text-white font-[Poppins] duration-500 px-6 py-2 mx-4 hover:bg-cyan-500 rounded">시작하기
      </button>
    </ul>
  </nav>
</body> -->

<!-- <Navbar bind:sidebar={open}/> -->

<svelte:window bind:scrollY={y} bind:innerHeight={innerHeight}/>

<div class="h-screen w-full flex flex-col">
  <div class="">

  <input id="my-drawer-3" type="checkbox" class="drawer-toggle" /> 
    <div class="drawer-content flex flex-col">
      <!-- Navbar -->
      <!-- <div class="w-full navbar bg-base-300 sticky top-0">
        <div class="flex-1 px-2 mx-2">꾸민</div>
        <div class="flex-none hidden lg:block">
          <ul class="menu menu-horizontal">
            <li><a>홈</a></li>
            <li><a>로그인</a></li>
          </ul>
        </div>
        <div class="flex-none lg:hidden ">
          <label for="my-drawer-3" class="btn btn-square btn-ghost">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" class="inline-block w-6 h-6 stroke-current"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path></svg>
          </label>
        </div> 
      </div> -->

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
              <p use:reveal={{ transition: "fade" }}>{@html src.text}</p>
              </div>
            {/if}
          </div>
        {/each}
      </Carousel>
      <!-- Page content here -->
      
      <!-- <h1 use:reveal>Your title</h1> -->
      
    </div> 
  </div>
</div>

<div id="">
  <div id="">
    <!-- <div id="img-container"
      style:transform="scale({calculate(y, 0, 1*innerHeight, 1, 1.5)})"
      style:opacity="{calculate(y, 0.7 * innerHeight, 1.8 * innerHeight, 1, 0)}"
      >
    </div> -->
    <div 
      id="img-container"
      style:opacity="{calculate(y + 700, 0.7 * innerHeight, 1.8 * innerHeight, 0, 1)}"
      >
    </div>
  </div>
</div>
<Example1 />


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

