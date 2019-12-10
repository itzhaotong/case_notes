# Sweetalert 弹框插件
## 官网 https://sweetalert.js.org/

## 引入CSS / JS
```html
<link href="plugins/sweetalert/sweetalert.css" rel="stylesheet">
<script type="text/javascript" src="plugins/sweetalert/sweetalert.min.js"></script>
```

## 单个提示使用方法
```
swal("系统提示","请输入账号!","warning");
```
![](https://s2.ax1x.com/2019/12/10/QDWIuq.png)

## 确认提示使用方法
```javascript
        swal({
	        title: "系统提示",
	        text: "确认要锁定 账号吗?",
	        icon: "warning",
	        buttons: true,
	        dangerMode: true,
	    }).then((flag) => {
	    	if(flag){
	    		 $.ajax({
                    type:  ,
                    url: "",
                    contentType: "application/json",
                    data: JSON.stringify(ids),
                    success: function (r) {
                        if (r.resultCode == 200) {
                            swal("锁定成功", { icon: "success",});
                        } else {
                            swal(r.message, {icon: "error",});
                        }
                    }
                });
	    	}
	    })
```
![](https://s2.ax1x.com/2019/12/10/QDfHsI.png)
![](https://s2.ax1x.com/2019/12/10/QDh2lj.png)