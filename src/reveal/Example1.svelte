<script>
	import { reveal } from 'svelte-reveal';
	import Label from './Label.svelte';

	import { onMount } from "svelte";
  let isMobile = false;

  // 모바일 환경 여부를 체크하는 함수
  function checkMobile() {
    isMobile = window.innerWidth < 768; // 예시로 768px보다 작으면 모바일로 간주
  }

  onMount(() => {
    checkMobile();
    window.addEventListener("resize", checkMobile);
    return () => {
      window.removeEventListener("resize", checkMobile);
    };
  });

</script>

<style>
	p {
		line-height: 1.75rem
	}
	
	h1 {
		display: block;
		font-size: 4rem;
		margin: 1.5rem 0;
	}
	
	h2 {
		font-size: 2.5rem;
		margin-bottom: 0;
	}
	
	h3 {
		font-size: 2rem;
		margin-bottom: 0;
	}
	
	.box {
		display: flex;
		gap: 1rem;
		margin-bottom: 2rem;
	}
</style>

<!-- <Label>Example 1</Label> -->
<!-- <h1 use:reveal={{ transition: "fade", delay: 50 }}>꾸민과 함께 꾸며!</h1>
<h2 use:reveal={{ delay: 100 }}>상상의 나래를 펼쳐~</h2>

<div class="box">
	<h3 use:reveal={{ delay: 600}}>이 글을 보게될 거에요~</h3>
	
</div> -->
<!-- <h3 use:reveal={{ delay: 100, x: -20, y: 20 }}>안녕하세요</h3> -->
<!-- <h3 use:reveal={{ transition: "fly", delay: 1300}}>blur !! 이어서 이 글까지요~</h3>
<h3 use:reveal={{ transition: "scale", delay: 1400}}>이어서 이 글까지요2~</h3>
<h3 use:reveal={{ transition: "blur", delay: 1400}}>이어서 이 글까지요2~</h3> -->

<!-- <p use:reveal={{ delay: 1800 }}>그렇죠? 😎</p> -->
<!-- <div class="flex place-items-center h-screen bg-blue-400 justify-center items-center">
  <div class="box">
		<div use:reveal={{ x: -10, y: 150 }}>
			<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FEWpzF%2FbtqGfMB0vZl%2FkqkwUwBXr2XyCQjNICA4x1%2Fimg.png" width=55% />
		</div>
		<div use:reveal={{ x: -10, y: 150 }}>
			<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FEWpzF%2FbtqGfMB0vZl%2FkqkwUwBXr2XyCQjNICA4x1%2Fimg.png" width=55% />
		</div>
	</div>
</div> -->






<!-- 카드 -->
<div class="h-screen w-screen w-full bg-gradient-to-r from-indigo-500 from-10% via-sky-500 via-30% to-emerald-500 to-90% flex flex-col justify-center items-center">
	<div class="card w-96 glass">
		<figure><img src="http://thescienceplus.com/news/data/20200810/p1065585306800416_891_thum.png" alt="car!"/></figure>
		<div class="card-body">
			<h2 class="card-title">고객관리</h2>
			<p>연락처부터 공사정보까지 꼼꼼하게~</p>
			<div class="card-actions justify-end">
				<button class="btn btn-primary">Learn now!</button>
			</div>
		</div>
	</div>
</div>




<div class="box h-screen w-screen w-full bg-gradient-to-r from-indigo-500 from-10% via-sky-500 via-30% to-emerald-500 to-90% flex flex-col justify-center items-center">
  <div class="w-full md:w-[80%] md:flex md:justify-center">
    {#if isMobile}
      <div use:reveal={{ x: -50, y: 10 }} class="md:w-full mb-4">
        <h3 use:reveal={{ transition: "blur", delay: 300 }} class="text-center text-white">간편하고 안전하게<br/>파트너를 찾아요!
      </div>
      <div use:reveal={{ x: -10, y: 150 }} class="md:w-full">
        <img class="max-w-full h-auto w-full" src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FEWpzF%2FbtqGfMB0vZl%2FkqkwUwBXr2XyCQjNICA4x1%2Fimg.png" />
      </div>
			
    {:else}
			<div use:reveal={{ x: -50, y: 10 }} class="md:w-full mb-4" >
        <h1
					use:reveal={{ transition: "blur", delay: 1000 }} 
					class="text-left text-white text-5xl font-fh font-bold leading-relaxed">간편하고 안전하게<br/>파트너를 찾아요!
				</h1>
				<h3
					use:reveal={{ transition: "blur", delay: 1500 }} 
					class="text-left text-white text-5xl font-fh font-bold leading-normal">어떤 인테리어 디자인이든<br/>이제 꾸민에게<br/>걱정없이<br/>파트너를 찾으실 수 있어요~
				</h3>
    	</div>

<!-- 'inset-0 flex justify-center text-3xl' : '' -->


      <div use:reveal={{ x: -10, y: 150 }} class="md:max-w-[50%] md:mr-2 mx-20 flex">
        <img class="max-w-full h-auto w-full md:w-[100%]" src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FEWpzF%2FbtqGfMB0vZl%2FkqkwUwBXr2XyCQjNICA4x1%2Fimg.png" />
      </div>
    {/if}
  </div>
</div>

<!-- 카드 -->
<div class="h-screen w-screen w-full bg-gradient-to-r from-emerald-400 from-10% via-sky-300 via-30% to-emerald-500 to-90% flex flex-col justify-center items-center">
	<div class="card w-96 glass">
		<figure><img src="http://thescienceplus.com/news/data/20200810/p1065585306800416_891_thum.png" alt="car!"/></figure>
		<div class="card-body">
			<h3 class="card-title">고객관리</h3>
			<p>How to park your car at your garage?</p>
			<div class="card-actions justify-end">
				<button class="btn btn-primary">Learn now!</button>
			</div>
		</div>
	</div>
</div>




<!-- 
<div class="box h-screen w-full  bg-blue-700 flex flex-col justify-center flex items-center ">
    <div class="flex items-center w-full md:flex md:justify-center">
				<div use:reveal={{ x: -50, y: 10 }} class="md:max-w-[50%] md:mr-2">
            <h3 use:reveal={{ transition: "blur", delay: 500 }}>간편하고 안전하게 파트너를 찾아요!</h3>
        </div>
        <div use:reveal={{ x: -10, y: 150 }} class="md:max-w-[50%] md:mr-2">
            <img class="max-w-full h-auto w-full md:w-[100%]" src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FEWpzF%2FbtqGfMB0vZl%2FkqkwUwBXr2XyCQjNICA4x1%2Fimg.png" />
        </div>
    </div>
</div>
 -->
