# Essential Vanilla JavaScript Functions
> Some of the missing functions implementation in JavaScript in vanilla form (inspired by [PHP](https://en.wikipedia.org/wiki/PHP)).

- Arrays
    - [`array_unique()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#array_unique) - Remove duplicates from an array
    - [`array_merge()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#array_merge) - Merge two arrays
    - [`array_chunk()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#array_chunk) - Splits an array into chunks of arrays
    - [`array_collapse()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#array_collapse) - Collapses a collection of arrays into a single, flat array
    - [`array_diff()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#array_diff) - Returns the values in the array1 that are not present in array2
    - [`array_intersect()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#array_intersect) - Returns the values common in the two supplied arrays
    - [`array_map()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#array_map) - Sends each value of an array to a user-made function, which returns new values
    - [`array_reject()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#array_reject) - Filters the array using the given callback. The callback should return true if the item should be removed from the resulting array
    - [`array_split()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#array_split) - Breaks an array into the given number of groups
    - [`array_take()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#array_take) - Returns a new array with the specified number of items
    - [`array_pad()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#array_pad) - Inserts a specified number of items, with a specified value, to an array
    - [`range()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#range) - Creates an array containing a range of elements
    
- String
    - [`chunk_split()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#chunk_split) - Splits a string into a series of smaller parts
    - [`str_pad()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#str_pad) - Pads a string to a new length
    - [`strrev()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#strrev) - Reverses a string
    - [`similar_text()`](https://github.com/amitmerchant1990/vanilla-javascript-functions#similar_text) - Calculates the similarity between two strings

## `array_unique()`
> Remove duplicates from an array
```js
function array_unique(arr){
    var seen = {};
    var ret_arr = [];
    var key;
    var i;

    function keyify(obj){
        var ret = "";
        var j;

        if (Object.prototype.toString.call(obj) === "[object Object]" || Object.prototype.toString.call(obj) === "[object Array]"){
            for (j in obj){
                ret += "~" + j + "^" + keyify(obj[j]) + "%";
            }
            return ret;
        }else{
          return obj;
        }
    }

    for(i = 0; i < arr.length; i++){
        key = keyify(arr[i]);
        if(!(key in seen)){
            ret_arr.push(arr[i]);
            seen[key] = true;
        }
    }

    return ret_arr;
}

array_unique([4,5,4,6,7,8,2,6]);
// [4, 5, 6, 7, 8, 2]
array_unique([{a: 'val'}, {b: 'val', c: 'val'}, 'a', 'b', [1,2,3,4], {a: 'val'}, [1,2,3,4], [{a: 'val'}, {b: 'val'}], [{a: 'val'}, {b: 'val'}]]);
// [{a: 'val'}, {b: 'val', c: 'val'}, 'a', 'b', [1,2,3,4], [{a: 'val'}, {b: 'val'}]]
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
>  Filters the array using the given callback. The callback should return `true` if the item should be removed from the resulting array
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

## `array_split()`
> Breaks an array into the given number of groups
```js
function array_split(arr, count){
    var temp_arr = [];
    var arr_length = arr.length;
    
    var chunk = Math.floor(arr_length/count);
    
    for(var i=0; i<arr.length;){
        var chunk_arr = [];
        
        if(temp_arr.length == (count-1))
            chunk = chunk + (arr_length-i);
        
        for(var j=0; j<chunk; j++){
            if(!arr[i])
                break;
            chunk_arr.push(arr[i]);
            i++;
        }
        
        temp_arr.push(chunk_arr);
    }
    
    return temp_arr;
}

array_split([1,2,3,4,5,6,7,8,9], 4);
// [ [ 1, 2 ], [ 3, 4 ], [ 5, 6 ], [ 7, 8, 9 ] ]
```

## `array_take()`
> Returns a new array with the specified number of items
```js
function array_take(arr, count){
    var temp_arr = [];
    
    if(count<0){
        count = Math.abs(count);
        for(var i=(arr.length-count); i<arr.length; i++){
            temp_arr.push(arr[i]);
        }
    }else{
        for(var i=0; i<count; i++){
            temp_arr.push(arr[i]);
        }
    }
    
    return temp_arr;
}

array_take([1,2,3,4,5,6,7,8,9], 4);
// [ 1, 2, 3, 4 ]
```
> You may also pass a negative integer to take the specified amount of items from the end of the array:
```js
array_take([1,2,3,4,5,6,7,8,9], -3);
// [ 7, 8, 9 ]
```

## `array_pad()`
> Inserts a specified number of items, with a specified value, to an array
```js

function array_pad(arr, size, value){
    for(var i=0; i<size; i++){
        arr.push(value);
    }
    return arr;
}

array_pad([1,2,3,4], 2, "unicorn");
// [ 1, 2, 3, 4, 'unicorn', 'unicorn' ]
```

## `range()`
> Creates an array containing a range of elements
```js
function range(start, end){
    var temp_arr = [];
    
    for(var i=start; i<=end; i++){
        temp_arr.push(i);
    }
    
    return temp_arr;
}

range(5, 11);
// [ 5, 6, 7, 8, 9, 10, 11 ]
```

## `chunk_split()`
> Splits a string into a series of smaller parts
```js
function chunk_split(string, length, end){
    var temp_string = '';
    
    for(var i=0; i<string.length; i++){
        temp_string += string[i];
        if((i+1)%length==0)
            temp_string += end;
    }
    
    return temp_string;
}

console.log(chunk_split("Hello", 1 , "."));
// H.e.l.l.o.
```

## `str_pad()`
> Pads a string to a new length
```js
function str_pad(string, size, value){
    for(var i=0; i<size; i++){
        string += value;
    }
    
    return string;
}

str_pad("unicorn", 5 , ".");
// unicorn.....
```

## `strrev()`
> Reverses a string
```js
function strrev(string){
    var temp_string = '';
    
    for(var i=string.length-1; i>=0; i--){
        temp_string += string[i];
    }
    
    return temp_string;
}

strrev("unicorn");
// nrocinu
```

## `similar_text()`
> Calculates the similarity between two strings
```js
function similar_text(string1, string2){
    var seen = {};
    var similar_count = 0;
    
    for(var i=0; i<string1.length; i++){
        if((string2.indexOf(string1[i]) !== -1 && !(string1[i] in seen)) 
                || string1[i]==' ')
        {
            similar_count++;
            if(string1[i]!='')
                seen[string1[i]] = true;
        }
    }
    
    return similar_count;
}

similar_text("Hello World","Hello Peter");
// 6
```

# License
MIT
