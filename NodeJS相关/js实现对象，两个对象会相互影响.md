今天在写堆的时候，打算用到对象来写，然后就用js简单实现了一个对象，但是途中遇到一个小问题，记录一下。

刚开始写的代码：
````
/**
 * Created by linSir on 17/2/11.
 */
function dui(list2) {
    this.list = list2;
    this._insert = function (data) {
        list.push(data);
        var i = list.length - 1;
        while (i / 2 >= 1) {

            if (list[i] > list[parseInt(i / 2)]) {
                var temp = list[i];
                list[i] = list[parseInt(i / 2)];
                list[parseInt(i / 2)] = temp;
            }
            i = i / 2;
        }

    }
    this.print = function () {
        console.log(list);
    }

}

var list = [0, 100, 90, 80, 65];
var _dui = new dui(list);
_dui.print();
var list2 = [0];
console.log(list2);
var _dui2 = new dui(list2);
_dui2._insert(100);
_dui2._insert(80);
_dui2._insert(65);
_dui2._insert(90);
_dui2.print();

````
这样写出来的代码，_dui,和_dui2是会想互影响的，查了一下才明白，是因为this.list = list2; 这句话，如果加上了this.的话，就会让这个list变成一个全局变量，大家访问的都是它，就不是对象的私有变量了。所以只需要去掉就可以了。
修改后：
````
/**
 * Created by linSir on 17/2/11.
 */
function dui(list2) {
    list = list2;
    this._insert = function (data) {
        list.push(data);
        var i = list.length - 1;
        while (i / 2 >= 1) {

            if (list[i] > list[parseInt(i / 2)]) {
                var temp = list[i];
                list[i] = list[parseInt(i / 2)];
                list[parseInt(i / 2)] = temp;
            }
            i = i / 2;
        }

    }
    this.print = function () {
        console.log(list);
    }

}

var list = [0, 100, 90, 80, 65];
var _dui = new dui(list);
_dui.print();
var list2 = [0];
console.log(list2);
var _dui2 = new dui(list2);
_dui2._insert(100);
_dui2._insert(80);
_dui2._insert(65);
_dui2._insert(90);
_dui2.print();

````

![运行结果 2017-02-11 下午11.47.44.png](http://upload-images.jianshu.io/upload_images/2585384-13838594afde9d7d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这样就好了，两个对象就不会相互造成干扰了。
