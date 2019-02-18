### 1. 模拟机操作
``` python
(1) rr 刷新程序
(2) ctrl + m 弹出操作菜单
(3) 
```
### 2. rn的margin和padding
``` python
(1)margin: 25;
(2)不支持margin: '25, 25, 25, 20';
(3) marginHorizontal: 40,
    marginVertical: 60
```
### 3. rn的border
``` python
(1)borderWidth: 2,
   borderColor: '#532aa3',
(2)不支持borderStyle
(3)borderLeftWidth: 3,
```
### 4. rn的position
``` python
(1)只有relative, absolute这两种
```
### 5. rn的display
``` python
(1)只有flex(默认), none这两种
```
### 6. rn的fontWeight
``` python
(1)fontWeight: 'bold'
(2)fontWeight: '100'
```
### 7. rn的阴影（只用于IOS）
``` python
(1) shadowColor: 'red'
(2) shadowOffset: {width: 10, height: 20}
(3) shadowOpacity: 0.5
(4) shadowRadius: 14
(5) 如果让android支持：
elevation: 20
(6)为了更好的支持Android： 使用 react-native-shadow
https://www.npmjs.com/package/react-native-shadow
```