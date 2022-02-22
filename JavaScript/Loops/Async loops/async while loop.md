```js
	const request = require('./request.js');
	
	const array = [1, 2, 3, 4, 5];
	
	(async function() {
		
		while (array.length > 0) {
		
		// Dequeue the first element in the array
		
		// Note that this modifies the array!
		
		const el = array.shift();
		
			const response = await request({
			
				method: 'GET',
				
				hostname: 'httpbin.org',
				
				path: '/get?myArg=' + el
			
			});
		
		const responseBody = JSON.parse(response.body);
		
		console.log(responseBody.args.myArg);
		
		}
	
	})()
```