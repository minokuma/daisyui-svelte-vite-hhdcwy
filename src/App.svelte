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
          <img src={src.url} alt={src.description} width=100% height={10} class=img-container  />
        {/if}
      </div>
    {/each}
  </Carousel>
    <div class="overlay-appbar-right">
      <div class="flex-none lg:hidden">
        <label for="my-drawer-3" class="btn btn-square btn-ghost">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" class="inline-block w-6 h-6 stroke-current"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path></svg>
        </label>
      </div>
    </div>
    <!-- Page content here -->
    <br/><br/><br/><br/><br/>
    <br/><br/><br/><br/><br/>
    <br/><br/><br/><br/><br/>
    <br/><br/><br/><br/><br/>
    <br/><br/><br/><br/><br/>
    <br/><br/><br/><br/><br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용<br/>
    내용<br/>내용<br/>내용<br/>내용<br/>내용10<br/>
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
            <label for="my-drawer-3" class="btn btn-square btn-ghost">
              <!-- svg 속성 -->
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" class="inline-block w-6 h-6 stroke-current"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
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
