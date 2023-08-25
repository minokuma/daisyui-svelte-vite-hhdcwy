<script>
	import { reveal } from 'svelte-reveal';
	import Label from './Label.svelte';
</script>

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
<p use:reveal={{ x: -50, y: 50 }}>
  <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FEWpzF%2FbtqGfMB0vZl%2FkqkwUwBXr2XyCQjNICA4x1%2Fimg.png" />
</p>


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