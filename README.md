# Vanilla JavaScript Functions


## `array_unique()`
> Remove duplicates from an array
```js
function array_unique(arr) {
    var seen = {};
    var ret_arr = [];
    for(var i=0; i<arr.length; i++){
        if(!(arr[i] in seen)){
            ret_arr.push(arr[i]);
            seen[arr[i]] = true;
        }
    }
    return ret_arr;
}

array_unique([4,5,4,6,7,8,2,6]);
// [4, 5, 6, 7, 8, 2]
```

## `array_merge()`
> Merge two arrays
```js
function array_merge(arr1, arr2){
    for(var i=0; i<arr2.length; i++){
        arr1.push(arr2[i]);
    }
    
    return arr1;
}

array_merge([1, 2, 3], [4, 5]);
// [1, 2, 3, 4, 5]
```

## `array_chunk()`
> Splits an array into chunks of arrays
```js
function array_chunk(arr, count){
    var temp_arr = [];
    
    for(var i=0; i<arr.length;){
        var chunk_arr = [];
        for(var j=0; j<count; j++){
            if(!arr[i])
                break;
            chunk_arr.push(arr[i]);
            i++;
        }
        temp_arr.push(chunk_arr);
    }
    
    return temp_arr;
}

array_chunk([1,2,3,4,5,6,7,8,9], 4);
// [ [ 1, 2, 3, 4 ], [ 5, 6, 7, 8 ], [ 9 ] ]
```

## `array_collapse()`
> Collapses a collection of arrays into a single, flat array
```js

function array_collapse(...arrays){
    var collapse_arr = [];
    
    for(var i=0; i<arrays.length;i++){
        for(var j=0; j<arrays[i].length; j++){
            collapse_arr.push(arrays[i][j]);
        }
    }
    
    return collapse_arr;
}

array_collapse([1, 2, 3, 4], [5, 6], ["hello", "world"]);
// [ 1, 2, 3, 4, 5, 6, 'hello', 'world' ]
```

## `array_diff()`
> Returns the values in the `arr1` that are not present in `arr2`
```js
function array_diff(arr1, arr2){
    var temp_arr = [];
    
    for(var i=0; i<arr1.length; i++){
        if(arr2.indexOf(arr1[i]) == -1){  
            temp_arr.push(arr1[i]);
        }
    }
    
    return temp_arr;
}

array_diff([4,5,6,7, "unicorn"], [5, 6, 7]);
// [ 4, 'unicorn' ]
```

## `array_intersect()`
> Returns the values common in the two supplied arrays
```js
function array_intersect(arr1, arr2){
    var temp_arr = [];
    
    for(var i=0; i<arr1.length; i++){
        if(arr2.indexOf(arr1[i]) != -1){  
            temp_arr.push(arr1[i]);
        }
    }
    
    return temp_arr;
}

array_intersect([4,5,6,7, "unicorn"], [5, 6, 7, 8]);
// [ 5, 6, 7 ]
```

## `array_map()`
> Sends each value of an array to a user-made function, which returns new values
```js
function array_map(arr, func){
    var temp_arr = [];
    
    if(typeof func !== "function")
        throw "Second parameter should be a function";
    
    for(var i=0; i<arr.length; i++){
        temp_arr.push(func(arr[i]));
    }
    
    return temp_arr;
}

array_map([1, 2, 3, 4, 5], function (value) {
    return value * 2;
});
// [ 2, 4, 6, 8, 10 ]
```

## `array_reject()`
>  Flters the array using the given callback. The callback should return `true` if the item should be removed from the resulting array
```js
function array_reject(arr, func){
    var temp_arr = [];
    
    if(typeof func !== "function")
        throw "Second parameter should be a function";
    
    for(var i=0; i<arr.length; i++){
        if(func(arr[i]))
            temp_arr.push(arr[i]);
    }
    
    return temp_arr;
}

array_reject([1, 2, 3, 4, 5], function (value) {
    return value > 3;
});
// [ 4, 5 ]
```
