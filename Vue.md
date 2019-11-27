##  

## VUE

```
Vue.js的指令是以v-开头的
- v-if指令
- v-show指令
- v-else指令
- v-for指令
- v-bind指令
- v-on指令
```

vue的script必须写在body下方，否则没效果

v-else元素必须立即跟在`v-if`或`v-show`元素的后面——否则它不能被识别 

Vue创建时需要传递的参数：el:你在标签上加的id  data自己需要的数据

```vue
new Vue({
	el :'#app'
	data: {				
		yes: true,				
		no: false,				
		age: 28,				
		name: 'keepfool'	
		message：“哈哈”	
		people: [{
        		name: 'Jack',
        		age: 30,
        		sex: 'Male'
        	}, {
        		name: 'Bill',
        		age: 26,
        		sex: 'Male'
        	}, {
        		name: 'Tracy',
        		age: 22,
       			sex: 'Female'
       		}, {
        		name: 'Chris',
        		age: 36,
        		sex: 'Male'
    		 }]	
	}

	methods: {
		greet: function() {
			// // 方法内 this 指向 vm
			alert(this.message)
		},
		say: function(msg) {
			alert(msg)
		}
	}
})

```

```
<div id="app">
			<h1>Hello, Vue.js!</h1>
			<h1 v-if="yes">Yes!</h1> //通过上方data定义的yes的值为true 那么v-if="yes(true)"
			<h1 v-if="no">No!</h1>//no就是false 所以这行不会显示
			<h1 v-if="age >= 25">Age: {{ age }}</h1> //28大于等于25 所以age会显示为28
			<h1 v-if="name.indexOf('jack') >= 0">Name: {{ name }}</h1>//名字没有包含jack所以不会显示
			<h1 v-show="yes">Yes!</h1>//v-show = true 那么Yes就会出来
			<h1 v-show="no">No!</h1>//false = 那么就不会出来No!
			<h1 v-if="age >= 25">Age: {{ age }}</h1>//如果28>=25就展示
			<h1 v-else>Name: {{ name }}</h1>//如果小于那么就显示keepfool
		</div>
		<tbody>
            <tr v-for="person in people">//将data中的people的每个下标的值赋给person
            <td>{{ person.name  }}</td>//那么person[0].name = Jack
            <td>{{ person.age  }}</td>
            <td>{{ person.sex  }}</td>
            </tr>
        </tbody>
        <button v-on:click="greet">Greet</button>//点击调用methon中的greet的message（哈哈）
        <!--缩写语法-->
		<button @click="greet">Greet</button>
        <button v-on:click="say('Hi')">Hi</button>//点击直接打印Hi
```

### demo

```
<!DOCTYPE html>
<html>

	<head>
		<meta charset="UTF-8">
		<title></title>
		<link rel="stylesheet" href="styles/demo.css" />
	</head>

	<body>
		<div id="app">

			<fieldset>
				<legend>
					Create New Person
				</legend>
				<div class="form-group">
					<label>Name:</label>
					<input type="text" v-model="newPerson.name"/>
				</div>
				<div class="form-group">
					<label>Age:</label>
					<input type="text" v-model="newPerson.age"/>
				</div>
				<div class="form-group">
					<label>Sex:</label>
					<select v-model="newPerson.sex">
					<option value="Male">Male</option>
					<option value="Female">Female</option>
				</select>
				</div>
				<div class="form-group">
					<label></label>
					<button @click="createPerson">Create</button>
				</div>
		</fieldset>
		<table>
			<thead>
				<tr>
					<th>Name</th>
					<th>Age</th>
					<th>Sex</th>
					<th>Delete</th>
				</tr>
			</thead>
			<tbody>
				<tr v-for="person in people">
					<td>{{ person.name }}</td>
					<td>{{ person.age }}</td>
					<td>{{ person.sex }}</td>
					<td :class="'text-center'"><button @click="deletePerson($index)">Delete</button></td>
				</tr>
			</tbody>
		</table>
		</div>
	</body>
	<script src="js/vue.js"></script>
	<script>
		var vm = new Vue({
			el: '#app',
			data: {
				newPerson: {
					name: '',
					age: 0,
					sex: 'Male'
				},
				people: [{
					name: 'Jack',
					age: 30,
					sex: 'Male'
				}, {
					name: 'Bill',
					age: 26,
					sex: 'Male'
				}, {
					name: 'Tracy',
					age: 22,
					sex: 'Female'
				}, {
					name: 'Chris',
					age: 36,
					sex: 'Male'
				}]
			},
			methods:{
				createPerson: function(){
					this.people.push(this.newPerson);
					// 添加完newPerson对象后，重置newPerson对象
					this.newPerson = {name: '', age: 0, sex: 'Male'}
				},
				deletePerson: function(index){
					// 删一个数组元素
					this.people.splice(index,1);
				}
			}
		})
	</script>

</html>
```



