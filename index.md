<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8" />
<link href="./css/common.css" rel="stylesheet" type="text/css" />

<script language="javascript" type="text/javascript"
	src="./js/jquery-1.7.2.js"></script>
<script type="text/javascript">

document.createElement("header");
document.createElement("section");
document.createElement("article");
document.createElement("footer");
document.createElement("menu");
document.createElement("aside");
document.createElement("nav");
document.createElement("hgroup");

</script>
<script language="javascript" type="text/javascript">
$(document).ready(function(){
     $("#nav > li").hover(
        function(){
            $(this).find(".child").show();
        },
        function(){
            $(this).find(".child").hide();
        }
    )
         
$("#securitySystem").find("a").each(function(n,value){
         $("#securitySystem_id").append("<a style='float:none;display:block' href='"+$(value).attr("href")+"'>"+$(value).attr("title")+"</a>");
});
    
         
  $("#productkinds").find("a").each(function(n,value){
        $("#productkinds_id").append("<a style='float:none;display:block' href='/dataAnalysis/index.jhtml?"+$(value).attr("id")+"'>"+$(value).attr("title")+"</a>") 
  }); 

  var winWidth = window.screen.width;


    var playID = false;
    var prevA  = $("#piclist a.previousA:first");
    var nextA  = $("#piclist a.nextA:first");
    var list   = $("#piclist ul:first");
    var step   = $("#piclist .step:first a")

    function fadeOpacity(objOut, objIn, n){
        objOut.animate({
            'opacity' : 0
        }, 600, function(){
            playID = false;
             $(this).removeClass("on");
        });
        objIn.animate({
            'opacity' : 1
        }, 600, function(){
           $(this).addClass("on");
        });

         step.removeClass("on");
        step.eq(n).addClass("on");
    }

    prevA.click(function(){
        if( !playID ){
            playID = true;
            var that = list.find("li[class*='on']");
            var n = that.index() <= 0 ? list.find("li").length - 1 : that.index() - 1;
            fadeOpacity(that, list.find("li").eq(n), n);
        }
        return false;
    });
    nextA.click(function(){
        if( !playID ){
            playID = true;
             var that = list.find("li[class*='on']");
            var n = that.index() >= (list.find("li").length-1) ? 0 : that.index() + 1;
            fadeOpacity(that, list.find("li").eq(n), n);
        }
        return false;
    });

    step.each(function(){
        $(this).click(function(){
            if( $(this).attr('class') != 'on' && !playID ){
                playID = true;
                var that = list.find("li[class*='on']");
                var n    = $(this).index();
                fadeOpacity(that, list.find("li").eq(n), n);
            }
            return false;
        })
    });

    setInterval(function(){
        if( !playID ){
            var that = list.find("li[class*='on']");
            var n = that.index() >= (list.find("li").length-1) ? 0 : that.index() + 1;
            fadeOpacity(that, list.find("li").eq(n), n);
        }
    }, 5000);
});

</script>
<title>花海株式会社</title>
</head>
<body>
	<header class="top" style="z-index: 2">
		<div class="header_content">
			<h1 class="logo">
				<a href="#"><img src="./image/logo.png" width="212" height="46" alt="sss" /></a>
			</h1>
			<nav>
				<ul id="nav">
					<li><a href="#" class="on">首页</a></li>
					<li><a href="#">产品</a>
						<div id="product_id" class="child">
							<ul style="margin-left: 750px;">
								<li><strong>产品</strong>
									<div id="productkinds_id"></div>
								</li>
								<li><strong>服务</strong>
									<div id="securitySystem_id"></div></li>
							</ul>
						</div>
					</li>
					<li><a href="#">关于我们</a>
						<div class="child">
							<ul style="margin-left: 900px;">
								<li><a href="#">公司简介</a></li>
								<li><a href="#">新闻活动</a></li>
								<li><a href="#">招贤纳士</a></li>
								<li><a href="#">联系我们</a></li>
							</ul>
						</div></li>
				</ul>
			</nav>
		</div>
	</header>

	<div id="product" style="display: none;"></div>

	<div id="productkinds" style="display: none;">
	   <a href="#" id="160" title="严选青汁"></a> <a
			href="#" id="162" title="母婴用品"></a>
	   <a href="#" id="163" title="电子产品"></a>
	</div>
	<div id="securitySystem" style="display: none;">
		<a href="#" title="中国直邮"></a> <a
			href="#" title="豪礼相送"></a> <a
			href="#" title="商品购买"></a>
	</div>
	<section class="focus_box">
		<div class="piclist" id="piclist">
			<ul>
				<li class="on"><a href="./image/focus01.jpg"
					style="background: url('./image/focus01.jpg') no-repeat center top;"></a>
				</li>
				<li><a href="./image/focus02.jpg"
					style="background: url('./image/focus02.jpg') no-repeat center top;"></a>
				</li>
				<li><a href="./image/focus03.jpg"
					style="background: url('./image/focus03.jpg') no-repeat center top;"></a>
				</li>
			</ul>
			<div class="shop">
				<a href="#" class="previousA"></a> <a href="#" class="nextA"></a>
				<div class="step">
					<a href="#" class="on"></a> <a href="#"></a> <a href="#"></a>
				</div>
			</div>
		</div>
	</section>

	<section class="content">
		<div class="fn_area">
			<aside>
				<img src="./image/service03.jpg" width="320" height="214" />
				<h3>
					<a href="#"
						title="最新新闻" target="_blank"> 最新新闻 </a>
				</h3>
				<p>喜报——日本保健歇会搭理推举产品...</p>
			</aside>
			<aside>
				<img src="./image/service02.jpg" width="320" height="214" />
				<h3>
					<a href="#"	title="推荐产品" target="_blank"> 推荐产品 </a>
				</h3>
				<p>严选青汁</p>
			</aside>
			<aside>
				<img src="./image/service01.jpg" width="320" height="214" />
				<h3>
					<a href="#" title=" 研制产品 " target="_blank"> 研制产品 </a>
				</h3>
				<p>海量产品研制生产...</p>
			</aside>
		</div>
	</section>

	<section class="intro">
		<table cellspacing="0" cellpadding="0" border="0">
			<tbody>
				<tr>
					<td width="55%">
						<div class="box">
							<p>
								<img src="./image/logo.png" width="140" height="30" alt="" />
							</p>
							<p><p>总部电话：12-345-67890123&nbsp;&nbsp;&nbsp;传真：12-345-67890123</p>
							<p>总部地址：日本福冈</p>
</p>
                    </div>
                    <img src="./image/code1.png" class="code" width=""	height="" alt="" />
                </td>
                <td width="80%">
							<a href="#">关于花海</a>
                   <p>
							<a href="#">招贤纳士</a>
						</p>
                    <p>
							<a href="#">联系我们</a>
						</p>
                </td>
            </tr>
        </tbody>
    </table>
</section>

<footer>2017 日本花海株式会社 版权所有</footer>

</body>
</html>
