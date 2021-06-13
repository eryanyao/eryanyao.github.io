---
layout: post
title: React Native 
---
Below will show some note that I write down when i learning react native. It contain some code, notes, documents, etc.



---
React Native Learning
# React Native 
- **useState**

```javascript
const  [name, setName] = useState('shaun');
const  [person, setPerson] = useState({name:  'morio fucker', age:  500});
const  clickHandler =  ()  =>  {
	setName('Yong');
	setPerson({name:'fucker bullshit', age:  4241});
}
```
- **stylesheet**
```javascript
const styles = StyleSheet.create({
	container:  {
		flex:  1,
		backgroundColor:  '#fff',
		alignItems:  'center',
		justifyContent:  'center',
	},
	item:  {
		marginTop:  24,
		backgroundColor:  'yellow',
		fontSize:  20,
	},
	header:  {
		backgroundColor:  'yellow',
		padding:  30,
	},
	boldText:  {
		fontWeight:  'bold',
	},
	buttonContainer:  {
		marginTop:  20,
	},
	input:  {
		borderColor:  'black',
		borderWidth:  1,
		padding:  10,
		margin:  10,
		width:  200,
	}
});
```
1. View
2. Text
3. Button
```javascript 
<Button  onPress={()  =>  submitHandler(text)} title='add todo'/> 
```
4. TextInput
```javacript
<TextInput 
	style={styles.input}
	placeholder='new todo item...'
	onChangeText={ changeHandler }    
 />
```
5. ScrollView
6. map
```javascript 
return (
	<View  style={styles.container}>
		<ScrollView>
			{people.map((item)  =>  {
			return (
				<View  key={item.key}>
					<Text  style={styles.item}>
					{item.name}
					</Text>
				</View>
			)
			})}
		</ScrollView>
	</View>
);
```
7. Flatlist
```javascript
<FlatList
	keyExtractor={(item)  =>  item.id}
	numColumns={2}
	data={people}
	renderItem={({item})=> (
	<Text  style={styles.item}>{item.name}</Text>
)} />
```
8. TouchableOpacity
```javascript
<TouchableOpacity  onPress={()  =>  pressHandler(item.id)}>
	<Text  style={styles.item}>{item.name}</Text>
</TouchableOpacity>
```
- filter
```javascript
const  pressHandler =  (id)  =>  {
	console.log(id);
	setPeople((prevPeople)  =>  {
	return  prevPeople.filter(person =>  person.id == id)
	})
}
```
## To do list
- show to do item
```javascript
//TodoItem
export  default  function  TodoItem({item, pressHandler}){
return (
	<TouchableOpacity  onPress={()  =>  pressHandler(item.key)}>
		<Text  style={styles.item}>{item.text} {item.key}</Text>
	</TouchableOpacity>
)
}
```
- add item
```javascript
//AddTodo
export  default  function  AddTodo({submitHandler}){
const  [text,setText] = useState('');
const  changeHandler =  (val)  =>  {
	setText(val);
}
return (
	<View>
		<TextInput
			style={styles.input}
			placeholder='new todo item...'
			onChangeText={ changeHandler }
			/>
		<Button  onPress={()  =>  submitHandler(text)} title='add todo'/>
	</View>
)
}
```
- App.js
```javascript 
import  TodoItem  from  './components/todo.js';
import  AddTodo  from  './components/addTodo';
```
```javascript 
const  [todos, setTodos] = useState([
{ text:  'task1', key:  '1'},
{ text:  'task2', key:  '2'},
{ text:  'task3', key:  '3'},
])

const  pressHandler =  (key)  =>  {
	setTodos((prevTodos)  =>  {
		return  prevTodos.filter(todo =>  todo.key != key);
	})
}

const  submitHandler =  (text)  =>  {
	setTodos((prevTodos)  =>  {
		return [
			{ text:  text, key:  Math.random().toString() },
			...prevTodos
		]
	})
}
```
```javascript
return (
<View  style={styles.container}>
	<Text>Open up App.js to start working on your app!</Text>
	<AddTodo  submitHandler={submitHandler}/>
	<View  style={styles.list}>
		<FlatList
		data={todos}
		renderItem={({item})  => (
		<TodoItem  item={item} pressHandler={pressHandler}/>
		)}
		/>
	</View>
</View>
);
```



