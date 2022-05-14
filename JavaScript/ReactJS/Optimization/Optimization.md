# Optimize your React Code


## Avoid recreation of values and components
- `Move your helper function` that is included in your React Functional Component `outside the component`. So the function is not recreated on every rerender.

- Avoid `nested components`: When you have a smaller component that is inside of another component, move this one outside the parent component, so it is not recreated every time. Pass the necessary dynamic values as props. 

- Memoization: 
	- Use the `useMemo` hook to preserve the expensive calculation's result during rerenders.
	- Use the `useCallback` hook to keep the functions (and not recreate them) as long as their dependencies change. 


## Avoid unnecessary markup
- Use the `<></>` react fragment instead of wrapper div elelements.  


## Speed up the start of your app 
- Use `code splitting`, create multiple JS files from your sourcecode with your bundler. 
	In webpeck when the async dynamic import is used, the bundler creates a separated JS file for that module. In ReactJS, this should be used with React.lazy but it is still experimental today (2022.03.01.) If you load your component this way, use the Suspense wrapper around the component to show a fallback UI during the async loading. 


## Code organization
- `Use barrels:` A barrel is a way to rollup exports from several modules into a single convenient module. **The barrel itself is a module file that re-exports selected exports of other modules**. So basically just create an index file inside your component's folder and reexport everything from there. 

- `Avoid prop drilling`: When you want to pass down a prop to a child that is far down in the component tree and the middle components do not need this prop use global state instead or React Context.

- `Avoid the too much prop on a component`: if you still want to keep all the props, use object, instead of a lot of separated props, and/or use spread operator to get a more concise and readable code. 

- `Do not use inline arrow function inside your components`:
Use [[Functional programming#Currying\Currying]] instead.
```jsx
const handleIt = (v: number) => { 
	return (e: any) => console.log(e, v);
}

return 
	<>
		<div>
			<input onChange={handleIt(1)} />
		</div>
	</>
```