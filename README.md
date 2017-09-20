# Vanilla JavaScript Functions


## `array_unique()`
> Remove duplicates from an array
```javascript
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

console.log(array_unique([4,5,4,6,7,8,2,6]));
// [4, 5, 6, 7, 8, 2]
```

## `array_merge()`
> Merge two arrays
```javascript
function array_merge(arr1, arr2){
    for(var i=0; i<arr2.length; i++){
        arr1.push(arr2[i]);
    }
    
    return arr1;
}

console.log(array_merge([1, 2, 3], [4, 5]));
// [1, 2, 3, 4, 5]
```

## `array_chunk()`
> Splits an array into chunks of arrays
```javascript
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


console.log(array_chunk([1,2,3,4,5,6,7,8,9], 4));
// [ [ 1, 2, 3, 4 ], [ 5, 6, 7, 8 ], [ 9 ] ]
```

## `array_collapse()`
> Collapses a collection of arrays into a single, flat array
```javascript

function array_collapse(...arrays){
    var collapse_arr = [];
    
    for(var i=0; i<arrays.length;i++){
        for(var j=0; j<arrays[i].length; j++){
            collapse_arr.push(arrays[i][j]);
        }
    }
    
    return collapse_arr;
}

console.log(array_collapse([1, 2, 3, 4], [5, 6], ["hello", "world"]));
// [ 1, 2, 3, 4, 5, 6, 'hello', 'world' ]
```

## `array_diff()`
> Returns the values in the `arr1` that are not present in `arr2`
```javascript
function array_diff(arr1, arr2){
    var temp_arr = [];
    for(var i=0; i<arr1.length; i++){
        if(arr2.indexOf(arr1[i]) == -1){  
            temp_arr.push(arr1[i]);
        }
    }
    
    return temp_arr;
}


console.log(array_diff([4,5,6,7, "unicorn"], [5, 6, 7]));
// [ 4, 'unicorn' ]
```
