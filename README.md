# Vanilla JavaScript Functions


## Remove duplicates from array
```javascript
function remove_duplicates(arr) {
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

console.log(remove_duplicates([4,5,4,6,7,8,2,6]));
// [4, 5, 6, 7, 8, 2]
```

## Merge two arrays
```javascript
function merge_array(arr1, arr2){
    for(var i=0; i<arr2.length; i++){
        arr1.push(arr2[i]);
    }
    
    return arr1;
}

console.log(merge_array([1, 2, 3], [4, 5]));
// [1, 2, 3, 4, 5]
```

## Array Chunk
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

## Array Collapse
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
