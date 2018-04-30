How about an inbuilt function to find the **depth** of an array, There is already an Experimental feature `Array.prototype.flatten(depth)`  which accepts a **depth** value up to which array needed to be **flatten**
But there is no inbuilt way to get the **depth** of an array. Currently to get the depth we have to do something like. which is an implicit way to get depth.
```js
function depthOf(arr) {
    if(!Array.isArray(arr))
        throw "Not an Array"
    var depth = 1;
    var i;
    for(var i = 0; i< arr.length; i++){
        if (!Array.isArray(arr[i])) continue;

        if(Array.isArray(arr[i])){
            var depth = depthOf(arr[i]) + 1;
            depth = Math.max(depth, depth);
        }
    }
    return depth;
}
```
If there is option to get **depth** explicitely that would be great. We already have property of array like `Array.length` why not have another property like `Array.depth`.

If we would have `Array.depth` property then code can look something like this.

> Note: below example caontains an experimental method of array `Array.prototype.flatten()`

```js
var arr1 = [1, 2, [3, 4, [5, 6]]];
arr1.flatten(arr1.depth);
// [1, 2, 3, 4, 5, 6]
```
