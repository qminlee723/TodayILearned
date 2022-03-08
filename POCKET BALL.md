# POCKET BALL



![image-20220306221145770](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220306221145770.png)

![image-20220306221425974](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220306221425974.png)

![image-20220306231201310](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220306231201310.png)



```python
import math
# 당일 날 제공되는 코드 상단에 import는 미리 정의되어있어요.

start = (1, 1)
end = (2, 2)

a = abs(end[0] - start[0])
b = abs(end[1] - start[1])

r = math.sqrt(a**2 + b**2)

radian = math.atan(b / a)
# degree 변환이 생각보다 많이 헷갈릴 수 있어요.
print(r, math.degrees(radian))
```

