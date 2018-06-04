var $body = $("body"),
	$index = $("#index"),
	$main = $("#main"),
	$cover = $("#cover"),
	$inCover = $(".inCover"),
	$page1 = $("#page1"),
	$page2 = $(".page2"),
	$second = $(".second"),
	$msecond = $(".msecond"),
	$leftHandBtn = $(".leftHandBtn"),
	$rightHandBtn = $(".rightHandBtn"),
	$lottery = $("#lottery"),//抽奖按钮
	$againBtn = $("#againBtn"),//再来一次
	$shareeatbtn = $("#shareeatbtn"),//粽情分享
	$shareCover = $(".shareCover"),
	$inShareCover2 = $(".inShareCover2"),
	$backgroundMusic = $("#backgroundMusic"),	
	$picState1 = $("#picState1"),
	$picState2 = $("#picState2"),
	$picState3 = $("#picState3"),
	$zongziCartoonIn2 = $(".zongziCartoonIn2"),
	inCoverText = 3,//透明框倒计时开始显示3
	count = 0,//切的数量
	shareMsg = "过端午，放“粽”切咸蛋，一起嗨起来！";
	
	//兼容不同手机
	(function (doc, win) {
  		var docEl = doc.documentElement,
   		resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
    	recalc = function () {
      	var clientWidth = docEl.clientWidth;
      	if (!clientWidth) return;
      		docEl.style.fontSize = 100 * (clientWidth / 320) + 'px';
    	};
  		if (!doc.addEventListener) return;
 			win.addEventListener(resizeEvt, recalc, false);
 			doc.addEventListener('DOMContentLoaded', recalc, false);
		})(document, window);


	
	//游戏5秒钟玩完，5秒倒计时事件;
	for(var i = 0 ; i < 5 ; i ++){
		$("<li>"+(4-i)+"</li>").appendTo($second);
		for(var j = 0 ; j < 10 ; j ++){
			$("<li>"+(9-j)+"</li>").appendTo($msecond);
		}
	}
	//触摸事件
	document.body.addEventListener('touchmove', function(event) { 
	    event.preventDefault();
	});
	//左手开始切
	$leftHandBtn[0].addEventListener('touchstart', function(event) {    
	    event.preventDefault();	 
	});
	//右手开始切
	$rightHandBtn[0].addEventListener('touchstart', function(event) {
	    event.preventDefault();	   
	});
	//左手离开屏幕
	$leftHandBtn[0].addEventListener('touchend', function(event) {
	    event.preventDefault();
	    acting("left");
	});
	//左手离开屏幕
	$rightHandBtn[0].addEventListener('touchend', function(event) {
	    event.preventDefault();
	    acting("right");
	});
	
	//游戏切蛋显示效果;
	function acting(gestures){
		if(gestures == "left"){
			$picState3.css("display","none");
			$picState2.css("display","block");//左
			$picState1.css("display","none");
		}else if(gestures == "right"){
			$picState3.css("display","none");
			$picState1.css("display","block");//右
			$picState2.css("display","none");
		}
		count ++;
		$("#count").text(count+"刀");
		//屏幕+咸蛋切的时候震动效果;
		if(count%2){
			$body.removeClass("shake").addClass("shake1");//整个屏幕震动
			$picState2.removeClass("wobble");
			$picState1.addClass("wobble");//右边咸蛋震动
		}else{	
			$body.removeClass("shake1").addClass("shake");//整个屏幕震动
			$picState1.removeClass("wobble");
			$picState2.addClass("wobble");//左边咸蛋震动
		}
	}	
	
	//不服再战
	$againBtn.click(function(){
		$main.animate({"-webkit-transform":"translateY(0)"},500,"ease",function(){
			$page1.addClass("fadeIn");
			$cover.css("display","block");
			inCoverText = 3;
			$inCover.text(inCoverText);			
			count = 0;//切的数量归0
			$("#count").text("");//清空游戏主页面显示的切蛋数量;
			$(".text").html("");
			$(".resultText").text("");//清空原来的文案:1.蛋都没碎，你行不行啊2、咸蛋已重伤，送往ICU3、咸蛋已被你虐烂了
			$picState3.css("display","block");
			$picState2.css("display","none");
			$picState1.css("display","none");
			$("#btnshow").css("width","0");
			gameStart();
		});
	});
	
	function gameStart(){
			$second.attr({"class":"second"});
			$msecond.attr({"class":"msecond"});
			$index.css("display","none");
			$main.css("display","block");
			$cover.css("display","block");	
			setTimeout(function(){
				$page1.addClass("fadeIn");
				$second.addClass("transition5");
				$msecond.addClass("transition5");
			},200);
			var timer3 = setInterval(function(){
				inCoverText -- ;
				$inCover.text(inCoverText);
			},1000);
	
			setTimeout(function(){
				try{
					$("#backgroundMusic")[0].play();
				}catch(e){
					console.log("error");
				}			
				clearInterval(timer3);
				$cover.css("display","none");
				$second.addClass("secondmove");
				$msecond.addClass("msecondmove");			
	
			var timer5 = setTimeout(function(){	
				try{
					$("#backgroundMusic")[0].pause();
					$("#backgroundMusic")[0].currentTime = 0;
				}catch(e){
					console.log("error");
				}				
				clearTimeout(timer5);	
				//时间结束，进入结果页
				$page1.removeClass("fadeIn");
				$main.animate({"-webkit-transform":"translateY(-33.33%)"},2000,"ease",function(){
					$page2.addClass("fadeIn");
					whatTheText(count);
					
				});			
			},5000);
				
		},3000);
	}
	
	//结果页显示事件；
	function whatTheText(n){
		$zongziCartoonIn2.css({"background-image":"url(style/images/egg01.png)","display":"block"});	
		$(".text").html("5秒切咸蛋" +"<b style='font-size:0.5rem;font-family: fantasy;'>"+ n + "</b>刀!!!");
		if(n>=20){
			$(".resultText").text("咸蛋已被你虐烂了~");
		}else if(n>=10){
			$(".resultText").text("咸蛋已重伤，送往ICU~");
		}else{
			$(".resultText").text("蛋都没碎，你行不行啊~");
		}
		shareMsg = "5秒切咸蛋" + n + "刀,一起来挑战吧!";		
		btnshow();
		shareWx();//结果页分享
	}
	//三个按钮延时出现
	function btnshow(){
		setTimeout(function(){
			$("#btnshow").animate({width:"100%"},200);
		},2000);
	}
	//分享页面事件
	$shareeatbtn.click(function(){
		$shareCover.css("display","block");
		$(".shareShowHide").css("display","block");
	
	});
	
	$inShareCover2.click(function(){
		$shareCover.css("display","none");
		$(".shareShowHide").css("display","none");
	});
	//抽奖显示页面时间
	$lottery.click(function(){
		$(".lotteryCover").css("display","block");
		$(".whiteDiv").css("display","block");
	});
	
	$(".closeLogo,.inlotteryCover2").click(function(){
		$(".lotteryCover").css("display","none");
		$(".whiteDiv").css("display","none");
	});	
	
	//规则显示隐藏;
	function rulesButton(){
		$("#guize").show();
	}
	function closeRule(){
		$("#guize").hide();
	}
	//微信事件
	/*var myURL = window.location.href.split('#')[0];		
	var enURL = encodeURIComponent(myURL);	
	
	//微信判别
	function isWeixin (){
		if(window.navigator.userAgent.indexOf("MicroMessenger") === -1 ){
			return false;
		}else{return true}
	}
	//微信检查并开启微信config	
	if(isWeixin()){		
		wxConfigToken (enURL);
	}else{		
		 wxConfigToken (enURL);
		alert("请在微信里打开");
	}
	function wxConfigToken (url){
		var xhr = new XMLHttpRequest();
		var url = url;
		xhr.open('get', '');   			
			xhr.setRequestHeader('Content-Type', 'application/json; charset=utf-8');
			xhr.onreadystatechange = function () {
			    if (xhr.readyState === 4 && xhr.status === 200) {			    
			    	shareWx();
			        result = JSON.parse(xhr.response);			   
			        wx.config({
			        	    debug: true, // 开启调试模式,调用的所有api的返回值会在客户端alert出来，若要查看传入的参数，可以在pc端打开，参数信息会通过log打出，仅在pc端时才会打印。
			        	    appId: '', // 必填，公众号的唯一标识
			        	    timestamp: '', // 必填，生成签名的时间戳
			        	    nonceStr: '', // 必填，生成签名的随机串
			        	    signature:'' ,// 必填，签名，见附录1
			        	    jsApiList: [
				                'onMenuShareTimeline',
				                'onMenuShareAppMessage',
				                'onMenuShareQQ',
				                'onMenuShareWeibo',				                				              			               
				                'closeWindow',				                
			              	] 
			        });
			    }
			}
		xhr.send();
	}
	
	function shareWx(){	
		wx.ready(function(){		   
		    wx.onMenuShareTimeline({
		        title:shareMsg, // 分享标题
		        link: myURL, // 分享链接
		        imgUrl: '../style/images/egg00.png', // 分享图标
		        success: function () { 
		            // 用户确认分享后执行的回调函数		            
		            return true;
		        },
		        cancel: function () { 
		            // 用户取消分享后执行的回调函数		          
		            return true;
		        }
		    });
			//微信分享事件;
		    wx.onMenuShareAppMessage({
		        title: '放“粽”切咸蛋', // 分享标题
		        desc: shareMsg, // 分享描述
		        link: myURL, // 分享链接
		        imgUrl: '../style/images/egg00.png', // 分享图标
		        type: 'link', // 分享类型,music、video或link，不填默认为link
		        dataUrl: '', // 如果type是music或video，则要提供数据链接，默认为空
		        success: function () { 
		            // 用户确认分享后执行的回调函数		          	      
		 	        return true;
		        },
		        cancel: function () { 
		            // 用户取消分享后执行的回调函数		           
		            return true;
		        }
		    });
	
		});
	}	
	*/
	