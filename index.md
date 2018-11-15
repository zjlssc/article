## js常用方法(待更新)
#### 检查手机号格式　
```javascript
function checkPhone (phone) {
  if (!(/^1[3|4|5|7|8|9][0-9]\d{8}$/.test(phone))) {
    return false
  } else {
    return true
  }
}

checkPhone(18923459876)
//true
checkPhone(12398762345)
//false
```
#### 数字格式化成千分位   
```javascript
function numToThousand(num) {
  if (!num) {
    return 0
  } else {
    return (num.toString().indexOf ('.') !== -1) ? num.toLocaleString() : num.toString().replace(/(\d)(?=(?:\d{3})+$)/g, '$1,')
  }
}
numToThousand(9876543)
// "9,876,543"
numToThousand(123456.76)
// "123,456.76"
```
#### 设置与获取sessionStorage
```javascript
//设置 data格式为json或字符串
function setSession (key, data) {
  window.sessionStorage.setItem(key, JSON.stringify(data))
}
//获取
function getSession (key) {
  return JSON.parse(window.sessionStorage.getItem(key))
}
setSession('name', 'tom')
getSession('name')
//tom
setSession('student', {name: tom,age: 18})
getSession('student')
//{name: tom,age: 18}
```
#### 时间戳转时间 
```javascript
function  dateFormat (timestamp) {
  if (timestamp) {
    let date = new Date(timestamp)
    let Y = date.getFullYear()
    let M = (date.getMonth() + 1 < 10 ? '0' + (date.getMonth() + 1) : date.getMonth() + 1)
    let D = date.getDate() < 10 ? '0' + date.getDate() : date.getDate()
    let h = date.getHours() < 10 ? '0' + date.getHours() : date.getHours()
    let m = date.getMinutes() < 10 ? '0' + date.getMinutes() : date.getMinutes()
    let s = date.getSeconds() < 10 ? '0' + date.getSeconds() : date.getSeconds()
    return Y + '-' + M + '-' + D + ' ' + h + ':' + m + ':' + s
  } else {
    return ''
  }
}
dateFormat(1542247446235)
// "2018-11-15 10:04:06"
dateFormat(new Date())
// "2018-11-15 10:05:13"
```
#### 从url中获取参数 返回值为一个对象
```javascript
function  getRequest () {
  let url = window.location.href
  let theRequest = {}
  if (url.indexOf('?') !== -1) {
    let str = url.split('?')[1]
    let strs = str.split('&')
    for (let i = 0; i < strs.length; i++) {
      theRequest[strs[i].split('=')[0]] = unescape(strs[i].split('=')[1])
    }
  }
  return theRequest
}
```
