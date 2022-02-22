```js
	const request = require('./request.js');
	
	function forEachWithCallback(callback) {
	
		const arrayCopy = this;
		
		let index = 0;
		
		const next = () => {
		
			index++;
			
			if (arrayCopy.length > 0) {
			
				callback(arrayCopy.shift(), index, next);
			
			}
		
		}
		
		next();
	
	}
	
	Array.prototype.forEachWithCallback = forEachWithCallback;
	
	const array = [1, 2, 3, 4, 5];
	
	array.forEachWithCallback(async (el, i, next) => {
	
		const response = await request({
		
			method: 'GET',
			
			hostname: 'httpbin.org',
			
			path: '/get?myArg=' + el
		
		});
		
		const responseBody = JSON.parse(response.body);
		
		console.log(responseBody.args.myArg);
		
		next();
	
	});

```