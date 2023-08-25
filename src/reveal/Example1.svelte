<script>
	import { reveal } from 'svelte-reveal';
	import Label from './Label.svelte';
</script>

<Label>Example 1</Label>
<h1 use:reveal={{ transition: "fade", delay: 50 }}>꾸민과 함께 꾸며!</h1>
<h2 use:reveal={{ delay: 100 }}>상상의 나래를 펼쳐~</h2>
<div class="box">
	<h3 use:reveal={{ delay: 600}}>이 글을 보게될 거에요~</h3>
	<h3 use:reveal={{ delay: 1200}}>이어서 이 글까지요~</h3>
  <h3 use:reveal={{ transition: "blur", delay: 1300}}>이어서 이 글까지요~</h3>
  <h3 use:reveal={{ transition: "scale", delay: 1400}}>이어서 이 글까지요2~</h3>
  <h3 use:reveal={{ transition: "fly", delay: 1400}}>이어서 이 글까지요2~</h3>
</div>
<p use:reveal={{ delay: 1800 }}>그렇죠? 😎</p>
<p use:reveal={{ delay: 2000 }}>
  <img src="https://img1.daumcdn.net/thumb/R1280x0/?fname=http://t1.daumcdn.net/brunch/service/guest/image/5rdoC4dVtpbnZRtlgnbSUJH59rM.png" />
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