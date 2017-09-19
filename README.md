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
```
