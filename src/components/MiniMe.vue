<template>
<div class="me me-con">
	<div class="me-body"></div>
	<div class="me-ponytail"></div>
	<div class="me-hair"></div>
	<div class="me-head"></div>
	<div class="me-bangs"></div>
	<div class="me-face">
		<div class="eyes"></div>
		<div class="cheeks"></div>
	</div>
</div>
</template>

<style type="text/css" lang="scss" scoped>

$flesh: #ffd7c5;
$hair:#292e48;
$shirt: #ff4f7f;
.pos {
	position:absolute;
	transform:translate(-50%, -50%);
	left:50%;
	top:50%;
}
.me-con {
	// @extend .pos;
	left: 0%;
	right: 0%;
	margin: auto;
	position:absolute;
	width:120px;
	height:120px;
	border: 1px solid rgba(255, 255, 255, 0.1);
	transition:all 0.2s;
	border-radius: 60px;
	top: 10%;
	margin: auto;

  @media only screen and (min-width: 600px) {
		bottom: 0%;
		top: 0%;
  }
	&.active {
		left:40%
	}
	&:hover{
		border-radius: 60px 60px 2px;
		cursor:pointer;
	}
}
.me-body {
	@extend .pos;
	width:6px;
	height:10px;
	background:$flesh;
	top:72%;
	box-shadow: inset 0px 6px 0px 0px $flesh - 30;
	&:before, &:after{
		content:"";
		position:absolute;
	}
	&:before {
		background:$flesh;
		width:6px;
		height:6px;
		border-radius:10px;
		top: 5px;
		z-index:1
	}
	&:after {
		width: 26px;
		height: 15px;
		background: $shirt;
		border-radius: 20px 20px 0px 0px;
		top: 7px;
		z-index: 0;
		left: -9px;
		box-shadow:inset 4px 0px 0px $shirt - 20
	}
}
.me-ponytail{
	@extend .pos;
	&:after{
		position:absolute;
		content:"";
		width:10px;
		height:20px;
		background:$hair;
		top:20px;
		left:-20px;
		border-radius: 0px 100px 0px 100px;
		transform: rotate(30deg);
	}
}
.me-head {
	@extend .pos;
	background:$flesh;
	border-radius:100px;
	height:50px;
	width:40px;
	&:after, &:before {
		content:"";
		top:-5px;
		left:0px;
		width:16px;
		height:26px;
		background:$hair;
		position:absolute;
		border-radius: 1px 10px 0px 10px;
		transform: rotate(53deg);
	}
	&:after{
		top:-8px;
		left:20px;
		width:20px;
		height:35px;
		border-radius: 10px 10px 10px 0px;
		transform: rotate(-50deg);
	}
}
.me-hair {
	@extend .pos;
	width:55px;
	height:50px;
	background:$hair;
	border-radius:80px;
	top:44%;
	&:after, &:before{
		content: "";
		left: -2px;
		top: 28px;
		width: 10px;
		height: 13px;
		background: $flesh;
		position: absolute;
		border-radius: 5px;
	}
	&:after {
		left:46px
	}
}
.me-bangs {
	@extend .pos;
	&:before, &:after{
		content: "";
		position: absolute;
		height: 36px;
		width: 10px;
		background: $hair;
		left: -27px;
		top: -12px;
		border-radius: 24px 0px 0px 24px;
		box-shadow:inset 2px -4px 0px $hair - 10
	}
	 &:after{
	    left: 14px;
	    width: 13px;
	    height: 39px;
	    border-radius: 0px 0px 100px 2px;
		box-shadow:none
	}
}

.me-face {
	@extend .pos;
	& .eyes {
		animation: blink 3s infinite;
		&:after,&:before {
			width:4px;
			height:15px;
			background:#000;
			position:absolute;
			content:"";
			left:-10px;
			top:-5px;
			border-radius:2px;
		}
		&:after {
			left:5px
		}
	}
	& .cheeks {
		&:after,&:before {
			width:8px;
			height:8px;
			background:#fa6363;
			position:absolute;
			content:"";
			left:-15px;
			top:10px;
			border-radius:4px;
		}
		&:after {
			left:6px
		}
	}
}

@keyframes blink  {
	0%{
		transform:scaleY(1)
	}	
	18%{
		transform:scaleY(1)
	}
	20%{
		transform:scaleY(0)
	}	
	25%{
		transform:scaleY(1)
	}	
	38%{
		transform:scaleY(1)
	}	
	40%{
		transform:scaleY(0)
	}	
	45%{
		transform:scaleY(1)
	}
	80% {
		transform:scaleY(1)
	}
}
</style>