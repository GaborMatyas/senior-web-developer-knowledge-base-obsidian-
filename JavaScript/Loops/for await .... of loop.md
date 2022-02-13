`for await` is supposed to be used with asynchronous iterators, not with arrays of pre-existing promises.

[async Iterators](https://www.mikealche.com/software-development/a-simple-explanation-of-the-for-await-of-statement-in-node-js)

```javascript
(async () => {
  for await (const commit of fetchCommits('javascript-tutorial/en.javascript.info')) {
    console.log(commit.author.login);
  }
})();
```


```javascript
for await (const res of items.map(e => somethingAsync(e))) …
```

works the same as

```javascript
const promises = items.map(e => somethingAsync(e));
for await (const res of promises) …
```

or

```javascript
const promises = [somethingAsync(items[0]), somethingAsync(items[1]), …];
for await (const res of promises) …
```


The `somethingAsync` calls are happening immediately, all at once, before anything is awaited. Then, they are `await`ed one after another, which is definitely a problem if any one of them gets rejected: it will cause an unhandled promise rejection error. **Using `Promise.all` is the only viable choice to deal with the array of promises**:

```javascript
for (const res of await Promise.all(promises)) …
```