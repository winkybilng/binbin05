# binbin05
<!DOCTYPE html>
<html>
<head>
	<title>binbin 05</title>
<style type="text/css">
	ul li{
		width: 30px;
		font-weight: bold;
		list-style-type: none;
		background-color: red;
		border: 1px solid #999;
		display: block;
		float: left;
		color: black;
		margin: 5px;
		text-align: center;
	}
</style>
</head>
<body>
<input type="text" name="input" id="text" value="请输入10到60之间的数字" onfocus="myFunction(this)">
<button id="left-in">左侧入</button>
<button id="left-out">左侧出</button>
<button id="right-in">右侧入</button>
<button id="right-out">右侧出</button>
<p id="erro"></p>
<ul id="line" style="position: absolute;">
	<li style="height: 30px ;margin-top:170px">10</li>
	<li style="height: 9px ;margin-top: 191px">3</li>
	<li style="height: 21px ;margin-top: 179px">7</li>
	<li style="height: 36px ;margin-top: 164px">12</li>
	<li style="height: 33px ;margin-top:167px">11</li>
	<li style="height: 90px ;margin-top: 110px">30</li>
</ul>
<script type="text/javascript">
	var a = document.getElementById("left-in");
	var b = document.getElementById("left-out");
	var c = document.getElementById("right-in");
	var d = document.getElementById("right-out");
	var e = document.getElementById("text");
	var f = document.getElementById("line");
	var ta = f.getElementsByTagName("li");
	var data = new Array;
	for (var i = 0; i < ta.length; i++) {
		data[i] = ta[i].innerHTML;
	}
//	document.getElementById("line").getElementsByTagName("li").style.height = "30px";
  // 可以通过数组方式，但是每次显示相当于重新加载整个列表。
	function render(data) {
		document.getElementById("erro").innerHTML = "";
		f.innerHTML = "";
		for (var i = 0; i < data.length; i++) {
			var b = document.createElement("b");
			f.appendChild(b);
			b.innerHTML = " <li style='margin-top:" +(200 - data[i]*3)+"px ;height:" + data[i]*3 + "px;'>"+data[i]+"</li>";
			//alert(f.innerHTML);
		}
	}
	function myFunction(x){
		x.value="";
	}
	c.onclick = function(){
		if (data.length<10) {
		if (e.value>=10&&e.value<=60) {
			data.push(e.value);
			render(data);
		} else {
			document.getElementById("erro").innerHTML = "请输入符合要求的数字";
		}
		} else {
			alert("再输入就是大傻傻！");
		}
	};
	a.onclick = function(){
		if (data.length<10) {
		if (e.value>=10&&e.value<=60) {
			data.unshift(e.value);
			render(data);
		} else {
			document.getElementById("erro").innerHTML = "请输入符合要求的数字";
		}
		} else {
			alert("再输入就是大傻傻！");
		}
	};
	b.onclick = function(){
		var item =data.shift();
		render(data);
		alert(item);
	};
	d.onclick = function(){
		var item =data.pop();
		render(data);
		alert(item);
	};
</script>
</body>
</html>
