# Promises

Basic Syntax

```js
fs.promises.readfile("my_file.txt", {encoding: "utf-8"})
.then((text) => {
	doSomething(text);
})
.catch((err) => {
	console.log(err);
});
otherstuff();

```

Chaining (Sequential Promises)

```js
fetch('crimes.json')
.then((response) => {
	return repsonse.json();
})
.then((data) => {
	return 
})
```

```js
Promise.all([fetch('/codes'), fetch('/neighborhoods'), fetch('/incidents')])
.then((response) => {
	return Promise.all([response[0].json(), response[1].json(), response[2].json()])
})
.then((data) => {
	// data[0] -> codes
	// data[1] -> neighborhoods
	// data[2] -> incidnents
})
```

# Async vs Sync
- All Synchronous code finishes before Asynchronous 