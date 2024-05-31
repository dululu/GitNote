# [unittest单元测试](https://github.com/dululu/Blogs/issues/43)

https://docs.python.org/3/library/unittest.html
### 文件结构
<img width="122" alt="image" src="https://github.com/dululu/notes/assets/64392262/56d6a8f6-480d-4373-bdaa-8f277bf58e52">

把`vector`文件夹变成一个`package`
<img width="121" alt="image" src="https://github.com/dululu/notes/assets/64392262/2cc1a2d9-9164-4c80-863e-f751845bb68c">
根目录下创建`tests`文件夹，放测试文件，变成一个`package`
#### `unittest` Python自带测试框架
```
python -m unittest   //根目录下运行，自动运行测试
```
### 写测试
- 每一个测试文件必须要是以`test_`开头
```
import unittest

# 要测试的函数
def add_numbers(a, b):
    return a + b

# 编写测试用例
class TestAddNumbers(unittest.TestCase):
    def test_add_numbers(self):
        result = add_numbers(3, 5)
        self.assertEqual(result, 8)  # 断言结果等于 8

        result = add_numbers(-2, 2)
        self.assertEqual(result, 0)  # 断言结果等于 0

        result = add_numbers(10, -7)
        self.assertEqual(result, 3)  # 断言结果等于 3

# 运行测试
if __name__ == '__main__':
    unittest.main()
```
- 继承` unittest.TestCase` 的测试类
- `test method`必须以`test_`开头
### 常用`feature`



---

https://cloud.tencent.com/developer/article/2127849