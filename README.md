<!--  index1.html   -->
<div class="iframe">
		<a href="javascript:;">我要改变你的颜色</a><br />
		<iframe id="childId" src="index2.html" frameborder="0"></iframe>
	</div>
	<script type="text/javascript">
		var chan = Channel.build({
		    window: document.getElementById("childId").contentWindow,
		    origin: "*",
		    scope: "yangyanyin",
		    onReady: function () {
		        //emit("channel is ready!");
		    }
		});

		var _the = true;
		$("a").click(function(){
			if(_the){
				var color = "#ff0000";
				chan.call({method: "area_tab", params:color, success: function () {}});
			}else{
				var color = "#444";
				chan.call({method: "area_tab", params:color, success: function () {}});
			}
			_the = !_the;
		})

		/*  var data = {
            id:a,
            style:file_style
        }
            chan.call({method: "init_draw", params: data,
            success: function (v) {
            }
        });  传个多值*/ 
	</script>
  
  <!-- index2 -->
  <div class="index2">
		我把你当兄弟，你既然跨越iframe修改我！！！！	
	</div>
	<script type="text/javascript">
		var chan = Channel.build({window: window.parent, origin: "*", scope: "yangyanyin"});
		chan.bind("area_tab", function (trans,color) {
		    $(".index2").css("color",color);
		});
	</script>
