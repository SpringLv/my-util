# (Object)对象的深度克隆
## 第一次看到深度克隆，不知道它要做什么.

    var a = 100;
    var b = a;
    var c = b - 1;
    console.log(a); //输出100，a还是a
    console.log(c); //99
    var x = {a:1,b:2};
    var y = x;
    delete y.a;
    var c = y;
    console.log(x); //{b:2},不存在承接的中间量，他们的指向是同一个对象（这个时候，想要不改变x的情况下，还要得到x的所有属性进行操作并生成新的对象，就要用到--深度克隆）
    console.log(c); //{b:2}
## ES5实现深度克隆
    var cloner = function(ob){
      var str, newob = ob.constructor === Array ? [] : {};
      if(typeof ob !== 'object'){
          return;
      } else if(window.JSON){
        str = JSON.stringify(ob);
        newob = JSON.parse(str);
      } else {
          for(var i in ob){
              newob[i] = typeof ob[i] === 'object' ? 
              cloner(ob[i]) : ob[i]; 
          }
      }
      return newob;
    }
## ES6实现克隆
    function clone(origin) {
      return Object.assign({}, origin);
    }
## bubbleSort冒泡
`
`function bubbleSort(arr) {
    `var len = arr.length;
    `for (var i = 0; i < len - 1; i++) {
        `for (var j = 0; j < len - 1 - i; j++) {
            `if (arr[j] > arr[j+1]) {        // 相邻元素两两对比
                `var temp = arr[j+1];        // 元素交换
                `arr[j+1] = arr[j];
                `arr[j] = temp;
            `}
        `}
    `}
    `return arr;
`}
`
