<script>
  import Carousel from "svelte-carousel";
  const images = [
    {
      url: "https://res.cloudinary.com/beswift/image/upload/v1650391490/photo-1644241687200-eadaf7601290_xcz2kh.jpg",
      description: "image1",
    },
    {
      url: "https://res.cloudinary.com/beswift/image/upload/v1650391337/photo-1647067867267-e01d98462f3c_ugtnwe.jpg",
      description: "image2",
    },
    {
      url: "https://res.cloudinary.com/beswift/image/upload/v1650391131/photo-1648800475313-2bb7fbec8701_ae60yw.jpg",
      description: "image3",
    },
    {
      url: "https://res.cloudinary.com/beswift/image/upload/v1650390102/photo-1649894222226-056a1a79d9fb_xlv73h.jpg",
      description: "image4",
    },
    {
      url: "https://res.cloudinary.com/beswift/image/upload/v1650389425/photo-1649894221695-45abb718a190_sgjhwd.jpg",
      description: "image5",
    },
  ];
  let carousel; // for calling methods of the carousel instance
  const handleNextClick = () => {
    carousel.goToNext();
  };
</script>

<div class="drawer drawer-end">
  <input id="my-drawer-3" type="checkbox" class="drawer-toggle" /> 
  
  <div class="drawer-content flex flex-col">
    <!-- Navbar start -->
    <nav class="sticky top-0">
      <div class="w-full navbar bg-base-300">
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
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" class="inline-block w-6 h-6 stroke-current"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path></svg>
          </label>
        </div>
      </div>
    </nav>
    <!-- Navbar  -->
    <Carousel
      bind:this={carousel}
      let:loaded
      autoplay
      autoplayDuration={3000}
      autoplayProgressVisible
    >
      {#each images as src, imageIndex (src)}
        <div class="img-container">
          {#if loaded.includes(imageIndex)}
            <img src={src.url} alt={src.description}  />
          {/if}
        </div>
      {/each}
  </Carousel>
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
    <ul class="menu w-full h-full bg-gray-100 text-gray-300">
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
