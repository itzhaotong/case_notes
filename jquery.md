# bootstrap的静态弹框

## 引用

```
<link href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/jquery@1.12.4/dist/jquery.min.js"></script>
<script src="http://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js"></script> 
```

## Js代码

```javascript
<script type="text/javascript">
    $(function(){
        $(".btn").click(function(){
            $("#mymodal").modal("toggle");
        });
        //触发id为addurl的点击方法
        $("#addurl").click(function(){ 
            //获取addurl的图片的src路径,并且赋值给id为urlpath的value属性
            $('#urlpath').val(('#addurl').attr('src'));
            //关闭静态弹窗(如果是打开的就关闭,如果是关闭就打开)
            $("#mymodal").modal("toggle");
        });
</script>
$('#urlpath').val(''); // 用法2 给input清空
$('#urlpath').val();  //  用法3 返回val的值
```

## CSS样式

```css
<style type="text/css">
    img{
        width: 150px;
        height: 50px;
    }
    ul{
        text-align:center;
    }
    urls{
        width: 500px;
        height: 300px;
        overflow-x: hidden;
        overflow-y: scroll;
        line-height: 30px;
        text-align: center;
    }
    </style>
```



## html代码

```html
<body class="hold-transition skin-red sidebar-mini">
		<div class="tetil">
			<h1>图文推送</h1>
		</div>
		<div class="center-block">
			<form>
			  <div class="form-group" id="btn">
			    <label for="exampleInputEmail1">图片地址</label>
			    <input type="text" class="form-control" id="urlpath" placeholder="点击选择或切换">
			  </div>
			  <button type="submit" class="btn btn-default">提交</button>
			</form>
		</div>
		<div class="modal" id="mymodal">
		    <div class="modal-dialog">
		        <div class="modal-content">
		    		<div class="modal-header">
						<button type="button" class="close" data-dismiss="modal"><span aria-hidden="true">&times;</span><span class="sr-only">Close</span></button>
						<h4 class="modal-title">选择图片</h4>
					</div>
					<div class="modal-body">
						<table class="urls" >
							<ul><img id="addurl" src="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=1735688044,4235283864&fm=26&gp=0.jpg"></ul>
						</table>
					</div>
					<div class="modal-footer">
						<button type="button" class="btn btn-default" data-dismiss="modal">关闭</button>
						<button type="button" class="btn btn-primary">保存</button>
					</div>
				</div>
			</div>
		</div>
	</body>
```

