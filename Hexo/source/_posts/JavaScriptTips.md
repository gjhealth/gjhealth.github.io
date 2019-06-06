### javaScript 每周学习 Tips

#### 第一周 (19.05.13 ~19.05.17)

- 字符串拼接

```
const a = "world";
console.log(`hello ` + a);
//模板字符
const a = "world";
console.log(`hello ${a}`);
```

- 字符串换行

```
console.log("string text line 1\n" + "string text line 2");

console.log(`string text line 1
string text line 2`);
```

- 箭头函数

```
 function sum(a, b) {
   return a + b;
 }

 sum = (a, b) => a + b;
```

- 回调函数

```
function success() {
  console.log("wow sucess");
}

setTimeout(success, 100)
```

- Promise

```

var compare = function(value) {
  return new Promise(function(resolve, reject) {
    if (value > 100) {
      resolve("success");
    } else {
      resolve("fail");
    }
  });
};

compare(50).then(result => {
  if (result == "success") {
    console.log("happy");
  } else {
    console.log("cry");
  }
});

```
