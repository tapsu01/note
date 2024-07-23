# 

1. JavaScript - Generating combinations from n arrays with m elements [duplicate]

```js
function cartesian(...args) {
  var r = [], max = args.length-1;
  function helper(arr, i) {
    for (var j=0, l=args[i].length; j<l; j++) {
      var a = arr.slice(0); // clone arr
      a.push(args[i][j]);
      if (i==max)
        r.push(a);
      else
        helper(a, i+1);
    }
  }
  helper([], 0);
  return r;
}
cartesian([0,1], [0,1,2,3], [0,1,2]);
```

2. MYSQL FIX: The server requested authentication method unknown to the client

```sh
CREATE USER '[user]'@'[ip_address]' IDENTIFIED WITH mysql_native_password BY 'your_password';

GRANT ALL PRIVILEGES ON *.* TO '[user]'@'[ip_address]' WITH GRANT OPTION;

FLUSH PRIVILEGES;
```
