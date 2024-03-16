Hello GitHub! 👋

<!--
**lichenyichay/lichenyichay** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
自我介绍:
我是chay，这是我的Github账号。
我会编程。
我会的语言：中文、英文。
我会的编程语言：Python、C++、C语言、Html、Java、Android（会一丢丢）。
我的学而思编程社区主页：https://code.xueersi.com/space/13438784
我的小码王编程社区主页：https://world.xiaomawang.com/w/person/project/all/3146479
我的GitHub主页：https://github.com/lichenyichay
以下是我写的部分作品：
Python集：
1、多功能一体机2.4.0（上载至pypi,持续更新）
```python
# -*- coding:UTF-8 -*-
# @Author:Chay
# @TIME:2022/12/26 10:43
# @FILE:main.py
# @Software:IDLE 3.11.1

import os,math,random,shutil,time,csv
book = {}   # 书名字典，格式：书名:本数
jiebook = {} # 借书清单

def jieshu(name,count):          #借书
    if name in book.keys():
        if book[name] < 0:
            del book[name]
        if name not in jiebook.keys():
            book[name] -= count
            jiebook.update({name:1})
            if book[name] < 0:
                del book[name]
            print("借书成功！")
            return 0
        else:
            print("请先还书后再借阅，操作失败！")
            return 1
    else:
        print("书目不存在，操作失败！")
        return 1
def huanshu(name,count):          #还书
    if name in book.keys():
        if name in jiebook.keys():
            book[name] += count
            jiebook[name] -= count
            if book[name] < 0:
                del book[name]
            if jiebook[name] < 0:
                del jiebook[name]
            print("还书成功！")
            return 0
        else:
            print("未查询到借阅记录，无法还书，操作失败！")
            return 1
    else:
        print("书目不存在！")
        return 1
def jiashu(name,count):          #在库存内加书
    if name in book.keys():
        book[name] += count
    else:
        book[name] = count
    print("操作成功！")
    return 0
def jianshu(name,count):       #在库存内减书
    if name in book.keys():
        book[name] -= count
        if book[name] < 0:
            del book[name]
        print("操作成功！")
        return 0
    else:
        print("书目不存在，操作失败！")
        return 1
def jiebooksavetocsv(mode):
    try:
        with open("D:\\图书管理系统\\借书清单.csv",mode,encoding="UTF-8",newline="") as f:
            csv_writer = csv.writer(f)
            for i in jiebook:
                csv_writer.writerow([i,jiebook[i]])
    except:
        with open("D:\\图书管理系统\\借书清单.csv","w",encoding="UTF-8",newline="") as f:
            csv_writer = csv.writer(f)
            csv_writer.writerow(["书名","本数"])
            for i in jiebook:
                csv_writer.writerow([i,jiebook[i]])
def booksavetocsv(mode):
    try:
        with open("D:\\图书管理系统\\图书清单.csv",mode,encoding="UTF-8",newline="") as f:
            csv_writer = csv.writer(f)
            for i in book:
                csv_writer.writerow([i,book[i]])
    except:
        with open("D:\\图书管理系统\\图书清单.csv","w",encoding="UTF-8",newline="") as f:
            csv_writer = csv.writer(f)
            csv_writer.writerow(["书名","本数"])
            for i in book: 
                csv_writer.writerow([i,book[i]])
def printjiebook():
    print("------借书清单------")
    print("书名          本数")
    for i in jiebook:
        print(i,"        ",jiebook[i])
    jiebooksavetocsv("w")
    return 0
def bookquery(name):
    a = {}
    for i in book.keys():
        if name in i:
            a[i] = book[i]
    if len(a) != 0:
        print("------查询结果------")
        print("书名          本数")
        for i in a:
            print(i,"        ",a[i])
    else:
        print("查询失败！")
        return 1
    return 0
def printbook():
    print("------库存清单------")
    print("书名          本数")
    for i in book:
        print(i,"        ",book[i])
    booksavetocsv("w")
    return 0
def startmenu():
    print("------处理原数据------")
    print("1、初始化（删除）")
    print("2、保留")
    return 0


'''
函数名：menu
调用形式：menu()
:param 无
:return 0
作用：输出主菜单
'''
def menu():
    print("------多功能一体机------")
    print("序号          功能")
    print("1             小工具合集")
    print("2             图形计算器")
    print("3             多功能计算器")
    print("4             math库专用计算器")
    print("5             小学学生信息管理系统")
    print("6             图书管理系统")
    print("7             退出")
    return 0

'''
函数名：xiaogongjumenu
调用形式：xiaogongjumenu()
:param 无
:return 0
作用：输出小工具合集菜单
'''
def xiaogongjumenu():
    print("------小工具合集------")
    print("序号          功能")
    print("1             抽取随机数")
    print("2             大小写转换")
    print("3             求最大公因数")
    print("4             求最小公倍数")
    print("5             取余")
    print("6             向下取整")
    print("7             向上取整")
    print("8             多个数求和")
    print("9             多个数求差")
    print("10            多个数求积")
    print("11            二分查找")
    print("12            判断闰年")
    print("13            判断是否为质数")
    print("14            返回上一级")
    return 0

'''
函数名：calculatormenu
调用形式：calculatormenu()
:param 无
:return 0
作用：输出多功能计算器菜单
'''
def calculatormenu():
    print("------多功能计算器------")
    print("序号          功能")
    print("1             整数、小数计算（加减乘除）")
    print("2             分数计算（加减乘除）")
    print("3             比大小")
    print("4             年龄计算")
    print("5             开平方")
    print("6             华氏度摄氏度转换")
    print("7             混合运算")
    print("8             货币换算")
    print("9             次方根")
    print("10            求解二元一次方程")
    print("11            返回上一级")
    return 0

'''
函数名：int_float_cal_menu
调用形式：int_float_cal_menu()
:param 无
:return 0
作用：输出多功能计算器—整数、小数计算菜单
'''
def int_float_cal_menu():
    print("------整数、小数计算（加减乘除）------")
    print("序号             功能")
    print("1                除法")
    print("2                返回上一级")
    return 0

'''
函数名：fractions_menu
调用形式：fractions_menu()
:param 无
:return 0
作用：输出多功能计算器—分数计算菜单
'''
def fractions_menu():
    print("------分数计算（加减乘除）------")
    print("序号             功能")
    print("1                加法")
    print("2                减法")
    print("3                乘法")
    print("4                除法")
    print("5                返回上一级")
    return 0

'''
函数名：hybrid_computing_menu
调用形式：hybrid_computing_menu()
:param 无
:return 0
作用：输出多功能计算器—混合运算菜单
'''
def hybrid_computing_menu():
    print("------混合运算------")
    print("序号             功能")
    print("1                +-混合运算")
    print("2                +*混合运算")
    print("3                +/混合运算")
    print("4                -+混合运算")
    print("5                -*混合运算")
    print("6                -/混合运算")
    print("7                *+混合运算")
    print("8                *-混合运算")
    print("9                */混合运算")
    print("10               /+混合运算")
    print("11               /-混合运算")
    print("12               /*混合运算")
    print("13               //混合运算")
    print("14               返回上一级")
    return 0

'''
函数名：currency_conversion_menu
调用形式：currency_conversion_menu()
:param 无
:return 0
作用：输出多功能计算器—货币转换菜单
'''
def currency_conversion_menu():
    print("------货币转换------")
    print("序号             功能")
    print("1                CNY（人民币）->USD（美元）")
    print("2                CNY（人民币）->JPY（日元）")
    print("3                USD（美元）->CNY（人民币）")
    print("4                USD（美元）->JPY（日元）")
    print("5                JPY（日元）->CNY（人民币）")
    print("6                JPY（日元）->USD（美元）")
    print("7                CNY（人民币）->MOP（澳门元）")
    print("8                MOP（澳门元）->CNY（人民币）")
    print("9                CNY（人民币）->HKD（港元）")
    print("10               HKD（港元）->CNY（人民币）")
    print("11               CNY（人民币）->TWD（台币）")
    print("12               TWD（台币）->CNY（人民币）")
    print("13               CNY（人民币）->GBP（英镑）")
    print("14               GBP（英镑）->CNY（人民币）")
    print("15               CNY（人民币）->EUR（欧元）")
    print("16               EUR（欧元）->CNY（人民币）")
    print("17               返回上一级")
    return 0

'''
函数名：mathmenu
调用形式：mathmenu()
:param 无
:return 0
作用：输出math库计算器菜单
'''
def mathmenu():
    print("------math库计算器------")
    print("序号             功能")
    print("1                把y的正负号加到x的前面")
    print("2                求x的余弦")
    print("3                弧度x转换成角度")
    print("4                求数学常量e")
    print("5                求数学常量pi")
    print("6                求x的正切值")
    print("7                求x的平方根")
    print("8                求x的正弦值")
    print("9                角度x转换成弧度")
    print("10               求x的y次方")
    print("11               输出由x的小数部分和整数部分组成的元组")
    print("12               求x以a为底的对数")
    print("13               求x*（2**i）的值")
    print("14               求x是不是数字")
    print("15               求x是不是正无穷大或负无穷大")
    print("16               求x的阶乘")
    print("17               求x的绝对值")
    print("18               求math.e的x次方-1")
    print("19               求math.e的x次方")
    print("20               返回上一级")
    return 0

'''
函数名：student_menu
调用形式：student_menu()
:return 0
作用：输出学生信息管理系统菜单
'''
def student_menu():
    print("------学生信息管理系统------")
    print("序号             功能")
    print("1                查询学员信息")
    print("2                删除学员信息")
    print("3                新增学员信息")
    print("4                退出")
    return 0
'''
函数名：book_menu
调用形式：book_menu()
:return 0
作用：输出图书管理系统菜单
'''
def book_menu():
    print("------图书管理系统------")
    print("序号                  功能")
    print("1                     用户操作")
    print("2                     管理员操作")
    print("3                     退出")
    return 0
'''
函数名：yonghumenu
调用形式：yonghumenu()
:return 0
作用：输出图书管理系统-用户操作菜单
'''
def yonghumenu():
    print("------用户操作------")
    print("序号                  功能")
    print("1                     借书")
    print("2                     还书")
    print("3                     查询")
    print("4                     打印借书清单（同时保存至Excel）")
    print("5                     返回上一级")
    return 0
'''
函数名：guanliyuanmenu
调用形式：guanliyuanmenu()
:return 0
作用：输出图书管理系统-管理员操作菜单
'''
def guanliyuanmenu():
    print("------管理员操作------")
    print("序号                  功能")
    print("1                     加库存")
    print("2                     减库存")
    print("3                     打印现有图书清单（同时保存至Excel）")
    print("4                     查询")
    print("5                     修改管理员密码")
    print("6                     返回上一级")
def startmenu():
    print("------处理原数据------")
    print("1、初始化（删除）")
    print("2、继续上次操作")
    return 0
'''
函数名：randomint
调用形式：a = randomint(maxint,minint,mode)
:param maxint 随机数最大值
:param minint 随机数最小值
:param mode 模式 bin（二进制）/oct（八进制）/int（十进制）/hex（十六进制） 不在选择范围内则抛出异常
:return 随机数
作用：取不同进制的随机数
'''
def randomint(maxint,minint,mode):
    b = random.randint(minint,maxint)
    if mode == "bin":
        return bin(b)
    elif mode == "oct":
        return oct(b)
    elif mode == "int":
        return b
    elif mode == "hex":
        return hex(b)
    else:
        raise TypeError("TypeError:模式错误！")

'''
函数名：daorxiao
调用形式：daorxiao(mode)
:param mode 模式 datoxiao（大写转小写）/xiaotoda（小写转大写） 不在选择范围内则抛出异常
:return 0
作用：大小写转换
'''
def daorxiao(mode):
    zifugeshu = int(input("请输入字符个数"))
    if mode == "datoxiao":
        if zifugeshu > 1:
            for i in range(zifugeshu):
                zifu = input("请输入第" + str(i + 1) + "个字符")
                # zifu1 = ord(zifu)
                zifu1 = ord(zifu) + 32
                zifu1 = chr(zifu1)
                zongzifu = []
                zongzifu.append(zifu1)
            print("转换结果：",end = '')
            for j in zongzifu:
                print(j)
        else:
            zifu = input("请输入字符：")
            zifu1 = ord(zifu)
            zifu1 = zifu1 + 32
            zifu1 = chr(zifu1)
            print("转换结果：" + zifu1)
        return 0
    elif mode == "xiaotoda":
        if zifugeshu > 1:
            for i in range(zifugeshu):
                zifu = input("请输入第" + str(i + 1) + "个字符")
                # zifu1 = ord(zifu)
                zifu1 = ord(zifu) - 32
                zifu1 = chr(zifu1)
                zongzifu = []
                zongzifu.append(zifu1)
            print("转换结果：",end = '')
            for j in zongzifu:
                print(j)
        else:
            zifu = input("请输入字符：")
            zifu1 = ord(zifu)
            zifu1 = zifu1 - 32
            zifu1 = chr(zifu1)
            print("转换结果：" + zifu1)
        return 0
    else:
        raise Exception("Error:模式错误!")

'''
函数名：twonumbers_TheBiggestCommonfactor
调用形式：a = twonumbers_TheBiggestCommonfactor(num1,num2)
:param num1 第一个数
:param num2 第二个数
:return num1和num2的最大公因数
作用：求最大公因数
'''
def twonumbers_TheBiggestCommonfactor(num1,num2):
    lst = []
    for i in range(1,max(num1,num2)+1):
        if num1 % i == 0 and num2 % i == 0:
            lst.append(i)
    return max(lst)

'''
函数名：twonumbers_TheMinimumCommonmultiple
调用形式：a = twonumbers_TheMinimumCommonmultiple(num1,num2)
:param num1 第一个数
:param num2 第二个数
:return num1和num2的最小公倍数
作用：求最小公倍数
'''
def twonumbers_TheMinimumCommonmultiple(num1,num2):
    lst = []
    for i in range(1,max(num1,num2)+1):
        if num1 % i == 0 and num2 % i == 0:
            lst.append(i)
    return num1 * num2 // max(lst)

'''
函数名：FtemporCtemp
调用形式：a = FtemporCtemp(mode,FtemporCtemp)
:param mode 模式 ℃to℉（摄氏度转为华氏度）/℉to℃（华氏度转为摄氏度） 模式不在选择范围内会抛出异常
:return 转换后的温度（不带单位）
作用：华氏度与摄氏度转换
'''
def FtemporCtemp(mode,FtemporCtemp):
    if mode == "℃to℉":
        return FtemporCtemp*9/5+32
    elif mode == "℉to℃":
        return (FtemporCtemp-32)*5/9
    else:
        raise TypeError("TypeError:模式错误！")

'''
函数名：duihuan
调用形式：a = duihuan(mode,money)
:param mode 模式 1~16 对应不同的货币转换，汇率也不同 模式不在选择范围内会抛出异常
:param money 要兑换的金额（以模式箭头前的货币单位作为1单位量）
:return 转换后的货币数量
作用：货币交换
'''
def duihuan(mode,money):
    if mode == 1:
        return 0.1565 * money
    elif mode == 2:
        return 17.1278 * money
    elif mode == 3:
        return 6.9670 * money
    elif mode == 4:
        return 109.4451 * money
    elif mode == 5:
        return 0.0584 * money
    elif mode == 6:
        return 0.0091 * money
    elif mode == 7:
        return 1.1497 * money
    elif mode == 8:
        return 0.8640 * money
    elif mode == 9:
        return 1.2276 * money
    elif mode == 10:
        return 0.8146 * money
    elif mode == 11:
        return 4.6834 * money
    elif mode == 12:
        return 0.2135 * money
    elif mode == 13:
        return 0.1177 * money
    elif mode == 14:
        return 9.1443 * money
    elif mode == 15:
        return 0.1342 * money
    elif mode == 16:
        return 8.2470 * money
    else:
        raise TypeError("TypeError:模式错误！")

'''
函数名：tuxing
调用形式：tuxing(huida)
:param huida 图形
:return 0
作用：进行图形计算
'''
def tuxing(huida):
    while True:
        if huida == "长方体":
            huida1 = input("请输入计算的是体积、表面积、棱长总和、容积还是染色问题（包含底面，且长宽高均为整数）：")
            huida2 = float(input("请输入长："))
            huida3 = float(input("请输入宽："))
            huida4 = float(input("请输入高："))
            if huida1 == "体积":
                shuchu = huida2 * huida3 * huida4
                print("体积是：" + str(shuchu))
            elif huida1 == "表面积":
                shuchu = (huida2 * huida3 + huida2 * huida4 + huida3 * huida4) * 2
                print("表面积是：" + str(shuchu))
            elif huida1 == "染色问题":
                huida2 = int(huida2)
                huida3 = int(huida3)
                huida4 = int(huida4)
                if huida4 == 1:
                    print("4个面染色的小正方体有4个。")
                    print("3个面染色的小正方体有" + str((huida2 - 2) * 2 + (huida3 - 2) * 2) + "个。")
                    print("2个面染色的小正方体有" + str((huida2 - 2) * (huida3 - 2)) + "个。")
                else:
                    print("3个面染色的小正方体有8个。")
                    print("2个面染色的小正方体有" + str(((huida2-2)+(huida3-2)+(huida4-2))*4) +"个。")
                    print("1个面染色的小正方体有" + str(((huida2-2)*(huida3-2)+(huida2-2)*(huida4-2)+(huida3-2)*(huida4-2))*2) + "个。")
                    print("0个面染色的小正方体有" + str((huida2-2)*(huida3-2)*(huida4-2)) + "个")
            elif huida1 == "棱长总和":
                shuchu = (huida2+huida3+huida4)*4
                print("棱长总和是：" + str(shuchu))
            elif huida1 == "容积":
                shuchu = huida2*huida3*huida4
                print("容积是：" + str(shuchu))
            else:
                print("不支持此功能")
        elif huida == "正方体":
            huida1 = input("请输入计算的是体积、表面积、棱长总和、容积还是染色问题（包含底面，且长宽高均为整数）：")
            huida2 = float(input("请输入棱长："))
            if huida1 == "体积":
                shuchu = huida2 ** 3
                print("体积是：" + str(shuchu))
            elif huida1 == "表面积":
                shuchu = huida2 ** 2 * 6
                print("表面积是" + str(shuchu))
            elif huida1 == "棱长总和":
                shuchu = huida2 * 12
                print("棱长总和" + str(shuchu))
            elif huida1 == "容积":
                shuchu = huida2 ** 3
                print("容积是：" + str(shuchu))
            elif huida1 == "染色问题":
                huida2 = int(huida2)
                if huida2 == 1:
                    print("6个面染色的小正方体有1个")
                else:
                    print("3个面染色的小正方体有8个。")
                    print("2个面染色的小正方体有" + str((huida2-2)*12) + "个。")
                    print("1个面染色的小正方体有" + str((huida2-2)**2*6) + "个。")
                    print("0个面染色的小正方体有" + str((huida2-2)**3) + "个。")
            else:
                print("不支持此功能")
        elif huida == "正方形":
            huida1 = input("请输入计算的是面积、边长之和还是折纸盒问题（剪掉的只能是小正方形）：")
            huida2 = float(input("请输入边长："))
            if huida1 == "面积":
                shuchu = huida2**2
                print("面积是：" + str(shuchu))
            elif huida1 == "边长之和":
                shuchu = huida2*4
                print("边长之和是：" + str(shuchu))
            elif huida1 == "折纸盒问题":
                huida3 = float(input("请输入被剪掉的小正方形的边长："))
                V = (huida2-2*huida3)**2
                S = huida2**2-((huida3**2)*4)
                print("体积是：" + str(V) + "表面积是：" + str(S))
            else:
                print("不支持此功能！")
        elif huida == "长方形":
            huida1 = input("请输入计算的是面积、周长还是折纸盒问题（剪掉的只能是小正方形）：")
            huida2 = float(input("请输入长："))
            huida3 = float(input("请输入宽："))
            if huida1 == "面积":
                shuchu = huida2*huida3
                print("面积是：" + str(shuchu))
            elif huida1 == "周长":
                shuchu = (huida2+huida3)*2
                print("周长是：" + str(shuchu))
            elif huida1 == "折纸盒问题":
                huida4 = float(input("请输入被剪掉的小正方形的边长："))
                V = (huida2-(2*huida4))*(huida3-(2*huida4))
                S = huida2*huida3-(huida4**2*4)
                print("体积是：" + str(V) + "表面积是：" + str(S))
            else:
                print("不支持此功能！")
        elif huida == "平行四边形":
            huida1 = int(input("请输入要计算的是面积、周长还是折纸盒问题（剪掉的必须是平行四边形，且平行四边形的四条边长度均相等）"))
            huida2 = float(input("请输入底："))
            huida3 = float(input("请输入高："))
            huida4 = float(input("请输入斜边的长度："))
            if huida1 == "面积":
                shuchu = huida2*huida3
                print("面积是：" + str(shuchu))
            elif huida1 == "周长":
                shuchu = (huida2+huida4)*2
                print("周长是：" + str(shuchu))
            elif huida1 == "折纸盒问题":
                huida5 = float(input("请输入被剪掉的平行四边形的边长："))
                S = huida2*huida3-(huida4**2)*4
                V = huida5*((huida4-2*huida5)*(huida2-2*huida5))
                print(f"体积是：{str(V)},表面积是：{str(S)}")
            else:
                print("不支持此功能！")
        elif huida == "菱形":
            huida1 = input("请输入要计算的是面积还是周长：")
            huida2 = float(input("请输入底："))
            huida3 = float(input("请输入高："))
            if huida1 == "面积":
                shuchu = huida2*huida3
                print(f"面积是：{str(shuchu)}")
            elif huida1 == "周长":
                shuchu = huida2*4
                print(f"周长是：{str(shuchu)}")
            else:
                print("不支持此功能！")
        elif huida == "三角形":
            huida1 = input("请输入要计算的是面积还是周长：")
            huida2 = float(input("请输入底："))
            huida3 = float(input("请输入高："))
            if huida1 == "面积":
                shuchu = huida2*huida3/2
                print(f"面积是：{str(shuchu)}")
            elif huida1 == "周长":
                huida4 = float(input("请输入其中1条腰长："))
                huida5 = float(input("请输入另1条腰长："))
                shuchu = huida2+huida4+huida5
                print(f"周长是：{str(shuchu)}")
            else:
                print("不支持此功能！")
        elif huida == "梯形":
            huida1 = input("请输入要计算的是面积还是周长：")
            huida2 = float(input("请输入上底："))
            huida3 = float(input("请输入下底："))
            huida4 = float(input("请输入高："))
            if huida1 == "面积":
                shuchu = (huida2+huida3)*huida4/2
                print(f"面积是：{str(shuchu)}")
            elif huida1 == "周长":
                huida5 = float(input("请输入其中1条腰长："))
                huida6 = float(input("请输入另1条腰长："))
                shuchu = huida2+huida3+huida5+huida6
                print(f"周长是：{str(shuchu)}")
            else:
                print("不支持此功能！")
        elif huida == "圆形":
            huida1 = input("请输入要计算的是面积、周长、方中圆还是圆中方：")
            huida2 = float(input("请输入半径："))
            if huida1 == "面积":
                shuchu = 3.14*(huida2**2)
                print(f"面积是：{shuchu}")
            elif huida1 == "周长":
                shuchu = 2*3.14*huida2
                print(f"周长是：{shuchu}")
            elif huida1 == "方中圆":
                shuchu = 0.86 * (r ** 2)
                print(f"S阴 = {shuchu}")
            elif huida1 == "圆中方":
                shuchu = 1.14 * (r ** 2)
                print(f"S阴 = {shuchu}")
            else:
                print("不支持此功能！")
        else:
            print("暂不支持此图形的计算！！！")
            time.sleep(2)
            break
    return 0

'''
函数名：math_cal
调用形式：s = math_cal(mode,float1,float2)
:param mode 模式 1~19 模式不在此选择范围内会抛出异常
:param float1 float2 float型参数，根据模式的需求，如参数有空余，则空余参数添0即可，例：mode = 3:math_cal(3,5.2,0);
例2：mode = 4:math_cal(4,0,0);例3：mode = 1:math_cal(1,5.92,-8)
:return 结果
'''
def math_cal(mode,float1,float2):
    if mode == 1:
        return math.copysign(float1,float2)
    elif mode == 2:
        return math.cos(float1)
    elif mode == 3:
        return math.degrees(float1)
    elif mode == 4:
        return math.e
    elif mode == 5:
        return math.pi
    elif mode == 6:
        return math.tan(float1)
    elif mode == 7:
        return math.sqrt(float1)
    elif mode == 8:
        return math.sin(float1)
    elif mode == 9:
        return math.radians(float1)
    elif mode == 10:
        return math.pow(float1,float2)
    elif mode == 11:
        return math.modf(float1)
    elif mode == 12:
        return math.log(float1,float2)
    elif mode == 13:
        return math.ldexp(float1,float2)
    elif mode == 14:
        return not math.isnan(float1)
    elif mode == 15:
        return not math.isinf(float1)
    elif mode == 16:
        return math.factorial(int(float1))
    elif mode == 17:
        return math.fabs(float1)
    elif mode == 18:
        return math.exp1(float1)
    elif mode == 19:
        return math.exp(float1)
    else:
        raise TypeError("TypeError:类型错误！")

'''
函数名：erfenchazhao
调用形式：a = erfenchazhao(yuanlst,shengxulst,target)
:param yuanlst 原序列
:param shengxulst 升序列表（原序列改编）
:param target 查找值
:return 查找结果（索引，用时，次数）
作用：查找列表中的值
'''
def erfenchazhao(yuanlst,shengxulst,target):
    start_time = time.time()
    start = 0
    count = 0
    end = len(shengxulst)-1
    if target not in shengxulst:
        end_time = time.time()
        return "列表中未查找到目标值"+str(target)+"，共用时"+str(end_time-start_time)+"s，查找次数：0，索引：无"
    while True:
        count += 1
        mid = (start+end)//2
        if target < shengxulst[mid]:
            end = mid-1
            continue
        elif target > shengxulst[mid]:
            start = mid + 1
            continue
        else:
            end_time = time.time()
            return "列表中已查找到目标值"+str(target)+"，共用时"+str(end_time-start_time)+"s，查找次数："+ str(count) +"，原列表中索引："+str(yuanlst.index(target))


'''
函数名：student
调用形式：student()
作用：小学学生信息管理系统
'''
def student():
    try:
        stu = {}
        while True:
            os.system("cls")
            student_menu()
            ans = input("请输入序号：")
            if ans == "1":
                try:
                    a = input("请输入学员姓名：")
                    print(f"{a}的相关信息是：{stu[a]}")
                    input()
                except:
                    print("无此学生")
                    input()
            elif ans == "2":
                a = input("请输入要删除的学员姓名：")
                del stu[a]
                print(a,"的相关信息已经删除")
                input()
            elif ans == "3":
                a = input("请输入要添加的学员姓名：")
                b = input("请输入新增的学员信息：")
                stu[a] = b
                print(a,"的相关信息已添加")
                input()
            elif ans == "4":
                break
            else:
                print("序号错误！")
                input()
    except Exception as e:
        print(repr(e))
'''
函数名：yiyuanerci
调用形式：yiyuanerci(float1,float2,float3)
:param float1 系数1
:param float2 系数2
:param float3 系数3
:return x1 实数根1
:return x2 实数根2
作用：求解一元二次方程
'''
def yiyuanerci(float1,float2,float3):
    dlt = float2 ** 2 - 4 * float1 * float3
    x1 = (-float2 + math.sqrt(dlt)) / 2 / float1
    x2 = (-float2 - math.sqrt(dlt)) / 2 / float1
    return f"x1 = {x1},x2 = {x2}"

'''
函数名：main
:return 无
作用：主程序
'''
def main():
    while True:
        os.system("cls")
        menu()
        try:
            a = int(input("请输入序号："))
            if a == 1:
                while True:
                    os.system("cls")
                    xiaogongjumenu()
                    try:
                        xuhao = int(input("请输入序号："))
                        if xuhao == 1:
                            c = int(input("请输入最小值："))
                            d = int(input("请输入最大值："))
                            while True:
                                try:
                                    e = input("请输入模式（二进制：bin;八进制：oct,十进制：int，十六进制：hex）：")
                                    print(randomint(d,c,e))
                                    input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 2:
                            e = input("请输入服务：（可选项：大写转小写，小写转大写）")
                            while True:
                                if e == "大写转小写":
                                    try:
                                        daorxiao("datoxiao")
                                        input()
                                        break
                                    except Exception as e:
                                        print(rept(e))
                                elif e == "小写转大写":
                                    try:
                                        daorxiao("xiaotoda")
                                        input()
                                        break
                                    except Exception as e:
                                        print(repr(e))
                                        input()
                                else:
                                    pass
                        elif xuhao == 3:
                            while True:
                                try:
                                    f = int(input("请输入第一个数据："))
                                    g = int(input("请输入第二个数据："))
                                    print(twonumbers_TheBiggestCommonfactor(f,g))
                                    input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 4:
                            while True:
                                try:
                                    h = int(input("请输入第一个数据："))
                                    i = int(input("请输入第二个数据："))
                                    print(twonumbers_TheMinimumCommonmultiple(h,i))
                                    input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 5:
                            while True:
                                try:     
                                    w1 = int(input("被除数："))
                                    w2 = int(input("除数："))
                                    w3 = w1 % w2
                                    print(w3)
                                    input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 6:
                            while True:
                                try:
                                    w1 = float(input("请输入要取整的数"))
                                    print(int(w1))
                                    input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 7:
                            while True:
                                try:
                                    w1 = float(input("请输入要取整的数"))
                                    print(int(w1)+1)
                                    input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 8:
                            try:
                                b = []
                                c = int(input("请输入元素个数："))
                                for i in range(c):
                                    d = float(input("请输入元素："))
                                    b.append(d)
                                b = tuple(b)
                                b = math.fsum(b)
                                print(b)
                                input()
                            except Exception as e:
                                print(repr(e))
                                input()
                        elif xuhao == 9:
                            try:
                                b = 0
                                c = int(input("请输入元素个数："))
                                e = []
                                for i in range(c):
                                    d = float(input("请输入元素："))
                                    e.append(d)
                                b = e[0]
                                for i in range(c-1):
                                    b -= e[1+i]
                                print(b)
                                input()
                            except Exception as e:
                                print(repr(e))
                                input()
                        elif xuhao == 10:
                            try:
                                b = 0
                                c = int(input("请输入元素个数："))
                                e = []
                                for i in range(c):
                                    d = float(input("请输入元素："))
                                    e.append(d)
                                b = e[0]
                                for i in range(c-1):
                                    b *= e[1+i]
                                print(b)
                                input()
                            except Exception as e:
                                print(repr(e))
                                input()
                        elif xuhao == 11:
                            while True:
                                d = input("请输入是否运行（运行输yes，否则输no）：")
                                if d == "yes":
                                    a = []
                                    while True:
                                        i = input("请输入列表中的数据（-1代表结束）：")
                                        if i == "-1":
                                            break
                                        else:
                                            a.append(i)
                                    b = sorted(a)
                                    c = input("请输入查找值：")
                                    diaoyong = erfenchazhao(a,b,c)
                                    print(diaoyong)
                                    input()
                                elif d == "no":
                                    break
                                else:
                                    print("指令无效！")
                                    input()
                        elif xuhao == 12:
                            while True:
                                try:
                                    year = int(input("输入一个年份: "))
                                    if (year % 4) == 0:
                                       if (year % 100) == 0:
                                           if (year % 400) == 0:
                                               print("{0} 是闰年".format(year))   # 整百年能被400整除的是闰年
                                               input()
                                           else:
                                               print("{0} 不是闰年".format(year))
                                               input()
                                       else:
                                           print("{0} 是闰年".format(year))       # 非整百年能被4整除的为闰年
                                           input()
                                    else:
                                       print("{0} 不是闰年".format(year))
                                       input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 13:
                            while True:
                                try:
                                    # 用户输入数字
                                    num = int(input("请输入一个数字: "))
                                    # 质数大于 1
                                    if num > 1:
                                       # 查看因子
                                       for i in range(2,num):
                                           if (num % i) == 0:
                                               print(num,"不是质数")
                                               break
                                       else:
                                           print(num,"是质数")
                                           input()
                                           
                                    # 如果输入的数字小于或等于 1，不是质数
                                    else:
                                       print(num,"不是质数")
                                       input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 14:
                            break
                        else:
                            print("序号错误！")
                            input()
                    except Exception as e:
                        print(repr(e))
            elif a == 2:
                huida = input("请输入计算对象：")
                tuxing(huida)
                input()
            elif a == 3:
                while True:
                    os.system("cls")
                    calculatormenu()
                    try:
                        xuhao = int(input("请输入序号："))
                        if xuhao == 1:
                            while True:
                                os.system("cls")
                                int_float_cal_menu()
                                try:
                                    xuhao1 = int(input("请输入序号"))
                                    if xuhao1 == 4:
                                        eee = float(input("被除数："))
                                        aaa = float(input("除数："))
                                        qqq = eee / aaa
                                        print("等于",qqq)
                                        input()
                                    elif xuhao1 == 5:
                                        break
                                    else:
                                        print("序号错误！")
                                        input()
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 2:
                            while True:
                                os.system("cls")
                                fractions_menu()
                                try:
                                    xuhao1 = int(input("请输入序号"))
                                    if xuhao1 == 1:
                                        while True:
                                            try:
                                                qw = int(input("分母1："))
                                                sd = int(input("分子1："))
                                                ad = int(input("分母2："))
                                                df = int(input("分子2："))
                                                sva = (sd/qw)+(df/ad)
                                                print("等于",sva)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 2:
                                        while True:
                                            try:
                                                qw = int(input("分母1："))
                                                sd = int(input("分子1："))
                                                ad = int(input("分母2："))
                                                df = int(input("分子2："))
                                                sva = (sd/qw)-(df/ad)
                                                print("等于",sva)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 3:
                                        while True:
                                            try:
                                                qw = int(input("分母1："))
                                                sd = int(input("分子1："))
                                                ad = int(input("分母2："))
                                                df = int(input("分子2："))
                                                sva = (sd/qw)*(df/ad)
                                                print("等于",sva)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 4:
                                        while True:
                                            try:
                                                qw = int(input("分母1："))
                                                sd = int(input("分子1："))
                                                ad = int(input("分母2："))
                                                df = int(input("分子2："))
                                                sva = (sd/qw)/(df/ad)
                                                print("等于",sva)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 5:
                                        break
                                    else:
                                        print("序号错误！")
                                        input()
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 3:
                            while True:
                                try:
                                    a1 = float(input("第一个数："))
                                    a2 = float(input("第二个数："))
                                    if a1 > a2:
                                        print(a1,">",a2)
                                        input()
                                    if a1 < a2:
                                        print(a1,"<",a2)
                                        input()
                                    if a1 == a2:
                                        print(a1,"=",a2)
                                        input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 4:
                            while True:
                                try:
                                    q1 = int(input("你出生的年份："))
                                    q2 = int(input("现在的年份："))
                                    q3 = q2 -q1
                                    print("你现在是",q3,"岁")
                                    input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 5:
                            while True:
                                try:
                                    ws1 = int(input("要开平方的数："))
                                    we2 = ws1**0.5
                                    print("平方是：",we2)
                                    input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                            
                        elif xuhao == 6:
                            while True:
                                try:
                                    choose = int(input("请输入序号（1：华氏度转摄氏度，2：摄氏度转华氏度）："))
                                    if choose == 1:
                                        while True:
                                            try:
                                                Ftemp = float(input("请输入华氏度温度："))
                                                print(FtemporCtemp("℉to℃",Ftemp))
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                        break
                                    elif choose == 2:
                                        while True:
                                            try:
                                                Ctemp = float(input("请输入摄氏度温度："))
                                                print(FtemporCtemp("℃to℉",Ctemp))
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                        break
                                    else:
                                        print("序号无效！")
                                        input()
                                    
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 7:
                            while True:
                                os.system("cls")
                                hybrid_computing_menu()
                                try:
                                    xuhao1 = int(input("请输入序号"))
                                    if xuhao1 == 1:
                                        while True:
                                            try:
                                                az = float(input("第一个加数："))
                                                qa = float(input("第二个加数："))
                                                qz = float(input("减数："))
                                                qwe = az + qa - qz
                                                print("等于：",qwe)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 2:
                                        while True:
                                            try:
                                                qwert = float(input("第一个加数："))
                                                asdfg = float(input("第二个加数："))
                                                zxcvb = float(input("乘数："))
                                                qaws = (qwert + asdfg) * zxcvb
                                                print("等于",qaws)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 3:
                                        while True:
                                            try:
                                                qw1 = float(input("第一个加数："))
                                                qw2 = float(input("第二个加数："))
                                                qw3 = float(input("除数："))
                                                qw4 = (qw1 + qw2) / qw3
                                                print("等于：",qw4)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 4:
                                        while True:
                                            try:
                                                wa_1 = float(input("被减数："))
                                                wa_2 = float(input("减数："))
                                                wa_3 = float(input("加数："))
                                                wa_4 = wa_1 - wa_2 + wa_3
                                                print("等于：",wa_4)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 5:
                                        while True:
                                            try:
                                                az = float(input("被减数："))
                                                ax = float(input("减数："))
                                                ac = float(input("乘数："))
                                                av = (az - ax) *ac
                                                print("等于：",av)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 6:
                                        while True:
                                            try:
                                                sz = float(input("被减数："))
                                                sx = float(input("减数："))
                                                sc = float(input("除数："))
                                                sv = (sz - sx) / sc
                                                print("等于：",sv)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 7:
                                        while True:
                                            try:
                                                milk = float(input("第一个乘数："))
                                                start = float(input("第二个乘数："))
                                                all = float(input("加数："))
                                                one = milk * start + all
                                                print("等于：",one)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 8:
                                        while True:
                                            try:
                                                two = float(input("第一个乘数："))
                                                to = float(input("第二个乘数："))
                                                too = float(input("减数："))
                                                fors = two * to - too
                                                print("等于：",fors)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 9:
                                        while True:
                                            try:
                                                you = float(input("第一个乘数："))
                                                I = float(input("第二个乘数："))
                                                he = float(input("除数："))
                                                she = you * I / he
                                                print("等于：",she)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 10:
                                        while True:
                                            try:
                                                _1 = float(input("被除数："))
                                                _2 = float(input("除数："))
                                                _3 = float(input("加数："))
                                                _4 = _1 / _2 + _3
                                                print("等于：",_4)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 11:
                                        while True:
                                            try:
                                                sk1 = float(input("被除数："))
                                                sk2 = float(input("除数："))
                                                sk3 = float(input("减数："))
                                                sk4 = sk1 / sk2 - sk3
                                                print("等于：",sk4)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 12:
                                        while True:
                                            try:
                                                fish = float(input("被除数："))
                                                water = float(input("除数："))
                                                mm = float(input("乘数："))
                                                mu = fish / water * mm
                                                print("等于：",mu)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 13:
                                        while True:
                                            try:
                                                mum = float(input("被除数："))
                                                dad = float(input("第一个除数："))
                                                sister = float(input("第二个除数："))
                                                brother = mum / dad / sister
                                                print("等于：",brother)
                                                input()
                                                break
                                            except Exception as e:
                                                print(repr(e))
                                                input()
                                    elif xuhao1 == 14:
                                        break
                                    else:
                                        print("序号错误！")
                                        input()
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 8:
                            while True:
                                os.system("cls")
                                currency_conversion_menu()
                                try:
                                    choose = int(input("请输入序号："))
                                    if choose <= 16 and choose > 0:
                                        int1 = float(input("请输入金额："))
                                        print(duihuan(choose,int1))
                                        input()
                                    elif choose == 17:
                                        break
                                    else:
                                        print("序号错误！")
                                        input()
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 9:
                            while True:
                                try:
                                    sdf = float(input("数："))
                                    z = int(input("次方根："))
                                    z = z/z/z
                                    ghj = sdf ** z
                                    print("等于",ghj)
                                    input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 10:
                            while True:
                                try:
                                    a,b,c = map(int,input("请输入方程的三个系数：").split())
                                    print(yiyuanerci(a,b,c))
                                    input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif xuhao == 11:
                            break
                        else:
                            print("序号错误！")
                            input()
                    except Exception as e:
                        print(repr(e))
                        input()
            elif a == 4:
                while True:
                    os.system("cls")
                    mathmenu()
                    try:
                        choose = int(input("请输入序号："))
                        if choose in [1,10,12,13]:
                            while True:
                                try:
                                    g = float(input("请输入第一个参数："))
                                    h = float(input("请输入第二个参数："))
                                    print(math_cal(choose,g,h))
                                    input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                        elif choose in [2,3,6,7,8,9,11,14,15,16,17,18,19]:
                            while True:
                                try:
                                    g = float(input("请输入参数："))
                                    print(math_cal(choose,g,0))
                                    input()
                                    break
                                except Exception as e:
                                    print(repr(e))
                                    input()
                        elif choose in [4,5]:
                            print(math_cal(choose,0,0))
                            input()
                        elif choose == 20:
                            break
                        else:
                            print("序号错误！")
                            input()
                        
                    except Exception as e:
                        print(repr(e))
                        input()
            elif a == 5:
                student()
                input()
            elif a == 6:
                while True:
                    try:
                        try:
                            if os.path.exists("D:\\图书管理系统"):
                                while True:
                                    os.system("cls")
                                    startmenu()
                                    a = input("请输入序号：")
                                    if a == "1":
                                        shutil.rmtree("D:\\图书管理系统")
                                        password = 0
                                        password = input("请设置管理员密码：")
                                        os.makedirs("D:\\图书管理系统")
                                        with open("D:\\图书管理系统\\password.txt","w") as file:
                                            file.write(password)
                                        break
                                    elif a == "2":
                                        with open("D:\\图书管理系统\\借书清单.csv") as f:
                                            f_csv = csv.reader(f)
                                            headers = next(f_csv)
                                            for row in f_csv:
                                                jiebook[row[0]] = row[1]
                                        with open("D:\\图书管理系统\\图书清单.csv") as f:
                                            f_csv = csv.reader(f)
                                            headers = next(f_csv)
                                            for row in f_csv:
                                                book[row[0]] = row[1]
                                        break
                                    else:
                                        print("序号错误！")
                        except Exception as e:
                            print(repr(e))
                        os.system("cls")
                        try:
                            with open("D:\\图书管理系统\\password.txt","r") as file:
                                password = file.read()
                        except Exception:
                            password = input("请设置管理员密码：")
                            os.makedirs("D:\\图书管理系统")
                            with open("D:\\图书管理系统\\password.txt","w") as file:
                                file.write(password)
                        while True:
                            os.system("cls")
                            book_menu()
                            xuhao = input("请输入序号：")
                            if xuhao == "1":
                                try:
                                    while True:
                                        os.system("cls")
                                        yonghumenu()
                                        xuhao1 = input("请输入序号：")
                                        if xuhao1 == "1":
                                            a = input("请输入书本名称：")
                                            jieshu(a,1)
                                        elif xuhao1 == "2":
                                            a = input("请输入书本名称：")
                                            huanshu(a,1)
                                        elif xuhao1 == "3":
                                            a = input("请输入关键词：")
                                            bookquery(a)
                                        elif xuhao1 == "4":
                                            printjiebook()
                                        elif xuhao1 == "5":
                                            break
                                        else:
                                            print("序号不存在！")
                                except Exception:
                                    pass
                            elif xuhao == "2":
                                try:
                                    while True:
                                        os.system("cls")
                                        
                                        b = input("请输入管理员密码：")
                                        if b == password:
                                            os.system("cls")
                                            guanliyuanmenu()
                                            xuhao1 = input("请输入序号：")
                                            if xuhao1 == "1":
                                                a = input("请输入书本名称：")
                                                number = int(input("请输入本数："))
                                                jiashu(a,number)
                                            elif xuhao1 == "2":
                                                a = input("请输入书本名称：")
                                                number = int(input("请输入本数："))
                                                jianshu(a,number)
                                            elif xuhao1 == "3":
                                                printbook()
                                            elif xuhao1 == "4":
                                                a = input("请输入关键词：")
                                                bookquery(a)
                                            elif xuhao1 == "5":
                                                password = input("请设置新管理员密码：")
                                                with open("D:\\图书管理系统\\password.txt","w") as file:
                                                    file.write(password)
                                                print("修改成功！")
                                                input()
                                            elif xuhao1 == "6":
                                                break
                                            else:
                                                print("序号不存在！")
                                        else:
                                            print("密码错误！")
                                            break
                                except Exception:
                                    pass
                            elif xuhao == "3":
                                jiebooksavetocsv("w")
                                booksavetocsv("w")
                                break
                            else:
                                print("序号不存在！")
                                input()
                        break
                    except:
                        print(repr(e))
                
            elif a == 7:
                break
            else:
                print("序号错误！")
                input()
        except Exception as e:
            print(repr(e))
            input()
    print("感谢你的使用，再见！")
    input()
if __name__ == "__main__":
    main()


```
最新版可至如下网址查看(库文件)：
```
https://github.com/lichenyichay/All-in-one
```
2、math库运算器3.1（IDLE、学而思编程社区等所有可编写python代码的均有效）
```python
import math
def z():   
    while True:    
        a = input("请输入功能：")
        if a == "取大于等于x的最小的整数值":
            b = input("请输入数据：")
            b = math.ceil(float(b))
            print(b)
        elif a == "把y的正负号加到x的前面":
            b = float(input("请输入第一个数据："))
            c = float(input("请输入第二个数据："))
            d = math.copysign(b,c)
            print(d)
        elif a == "求x的余弦":
            b = input("请输入数据：")
            b = math.cos(float(b))
            print(b)
        elif a == "把x从弧度转换成角度":
            b = float(input("请输入数据："))
            b = math.degrees(b)
            print(b)
        elif a == "求数学常量e":
            b = math.e
            print(b)
        elif a == "求数学常量pi":
            b = math.pi
            print(b)
        elif a == "求x的整数部分":
            b = input("请输入数据：")
            b = math.trunc(float(b))
            print(b)
        elif a == "求x的正切值":
            b = input("请输入数据：")
            b = math.tan(float(b))
            print(b)
        elif a == "求x的平方根":
            b = float(input("请输入数据："))
            b = math.sqrt(b)
            print(b)
        elif a == "求x的正弦值":
            b = input("请输入数据：")
            b = math.sin(float(b))
            print(b)
        elif a == "角度x转换成弧度":
            b = input("请输入数据：")
            b = math.radians(float(b))
            print(b)
        elif a == "求x的y次方":
            b = float(input("请输入第一个数据："))
            c = float(input("请输入第二个数据："))
            d = math.pow(b,c)
            print(d)
        elif a == "输出由x的小数部分和整数部分组成的元组":
            b = float(input("请输入数据："))
            b = math.modf(b)
            print(b)
        elif a == "求x以a为底的对数":
            b = int(input("请输入第一个数据："))
            c = int(input("请输入第二个数据："))
            d = math.log(b,c)
            print(d)
        elif a == "求x*（2**i）的值":
            b = float(input("请输入第一个数据："))
            c = float(input("请输入第二个数据："))
            d = math.ldexp(b,c)
            print(d)
        elif a == "求x是不是数字":
            b = float(input("请输入数据:"))
            c = math.isnan(b)
            if c == True:
                print("不是数字")
            else:
                print("是数字")
        elif a == "求x是不是正无穷大或负无穷大":
            b = int(input("请输入数据："))
            b = math.isinf(b)
            if b == True:
                print("是正无穷大或负无穷大")
            else:
                print("不是正无穷大或负无穷大")
        elif a == "求(x的平方+y的平方)的值":
            b = float(input("请输入第一个数据："))
            c = float(input("请输入第二个数据："))
            d = math.hypot(b,c)
            print(d)
        elif a == "求x和y的最大公约数":
            b = int(input("请输入第一个数据："))
            c = int(input("请输入第二个数据："))
            d = math.gcd(b,c)
            print(d)
        elif a == "对多个元素进行求和":
            b = []
            c = int(input("请输入元素个数："))
            for i in range(c):
                d = int(input("请输入元素"))
                b.append(d)
            b = tuple(b)
            b = math.fsum(b)
            print(b)
        elif a == "求x/y的余数":
            b = float(input("请输入第一个数据："))
            c = float(input("请输入第二个数据："))
            d = math.fmod(b,c)
            print(d)
        elif a == "求小于等于x的最大的整数值":
            b = float(input("请输入数据："))
            b = math.floor(b)
            print(b)
        elif a == "求x的阶乘的值":
            b = int(input("请输入数据："))
            b = math.factorial(b)
            print(b)
        elif a == "求x的绝对值":
            b = float(input("请输入数据："))
            b = math.fabs(b)
            print(b)
        elif a == "求math.e的x次方减1":
            b = float(input("请输入数据："))
            b = math.exp1(b)
            print(b)
        elif a == "求math.e的x次方":
            b = float(input("请输入数据："))
            b = math.exp(b)
            print(b)
        else:
            print("暂不支持此功能！")
            break
z()
```
C++及C篇：
1、身份证验证真假修复版（多次）
```C++
#include <iostream>
#include <ctime>
using namespace std;

int main()
{
    int a,b;
    string id;
    cout << "请输入身份证号：";
    cin >> id;
    while (id!="-1"){
        //计算数的存储
        int jss[17]={7,9,10,5,8,4,2,1,6,3,7,9,10,5,8,4,2};
        //校验码的存储
        char jym[11]={'1','0','X','9','8','7','6','5','4','3','2'};
        int sum = 0;
        //补充完整计算的过程(for循环)
        for (int i = 0; i <= 16; i++) 
        {
            //1.身份证的字符型数字变为整型
            a = id[i] - '0';
            //2.整型数字乘以对应的计算数
            b = a * jym[i];
            //3.计算结果累加到sum中
            sum = sum + b;
            
                
        }
        //验证校验码内容
        int c = sum % 11;
        if (id[17] == jym[c])
        {
            cout << "验证结果：真\n";
        }
        else
        {
            cout << "验证结果：假\n";
            break;
        }
        al:{
            c=0;
            a=0;
            b=0;
            string id;
            cout << "请输入身份证号：";
            cin >> id;
            sum = 0;
            //补充完整计算的过程(for循环)
            for (int i = 0; i <= 16; i++) 
            {
                //1.身份证的字符型数字变为整型
                a = id[i] - '0';
                //2.整型数字乘以对应的计算数
                b = a * jym[i];
                //3.计算结果累加到sum中
                sum = sum + b;
                
                    
            }
            //验证校验码内容
            c = sum % 11;
            if (id[17] == jym[c])
            {
                cout << "验证结果：真\n";
                goto al;
            }
            else
            {
                cout << "验证结果：假\n";
                break;
            }
        }
        
    }
    
    return 0;
}
```
2、密码破译站1.3.2
```C++
#include <bits/stdc++.h>
#include <string>

using namespace std;
int ecpn = 1,c = 1,d = 1;
void download(){

    double download_step_list[6] = {0.0,5.34,6.30,11.50,13.905,30.89}; 
    int space = 0;
    cout << "\33[?25l";
    for(int i = 0;i < 6;i++){
        cout << "[" << "\33[42m" <<" 已下载：" << download_step_list[i] << "MB " << "\33[0m" <<"]" << download_step_list[5] << "MB" <<"/" << download_step_list[i] << "MB" << endl;
    
    
    }
    cout << "\33[?25h";
    cout << "下载成功！" << endl;

    
}
void ECPN(int choice_ecpn,string string_ecpn,int mode_ecpn){
    char sum_list[10000] = {0};
    int len_ecpn = string_ecpn.size();
    for(int i = 0;i < len_ecpn;i++){
        sum_list[i] = string_ecpn[i];    
    }

    cout << "结果是：" << endl;
    switch(choice_ecpn){
        case 1://KS3F
            for(int i = 0;i < len_ecpn;i++){
                if(mode_ecpn == 1){
                    sum_list[i] += 3;
                }else if(mode_ecpn == 2){
                    sum_list[i] -= 3;
                }
                cout << sum_list[i];
            }
            cout<< endl;
            break;
        case 2://NCSE
            char NCSE_char;
            int NCSE_num;
            for(int i = 0;i < len_ecpn;i++){
                if(mode_ecpn == 1) {
                    sum_list[i] = (int)sum_list[i];
                }else if(mode_ecpn == 2){
                    sum_list[i] = (char)sum_list[i];
                }
                cout << sum_list[i];
            }
            cout << endl;
            break;
        default:
            break;
    }
}

int main(){
    download();

    string input_string,user;
    cout << "请输入用户名：" << endl;
    getline(cin,user);
    cout << "Hello," << user << "." << endl;
    while(true){
        
    
        int choice;
        cout << "1.解码 2.加密 3.设置解码方式 0.退出 请输入：";
        cin >> choice;
        if(choice == 0){
            exit(0);   
        }else if(choice == 1){
            c = 1;
            cout << "请输入要处理的字符串：" << endl;
            cin >> input_string;
            ECPN(c,input_string,d);
        }else if(choice == 2){
            c = 2; 
            cout << "请输入要处理的字符串：" << endl;
            cin >> input_string;
            ECPN(c,input_string,d);
        }else if(choice == 3){
            cout << "请选择处理方式：1.KS3F 2.NCSE" << endl;
            cout << "当前处理方式为：";
            if(d == 1){
                cout << " KS3F" << endl;
            }else{
                cout << " NCSE" << endl;
            }
            cin >> d;
            if(d!=1 && d!=2){
                cout << "输入错误！" << endl;
                break;
            }
        }
    
    }
    return 0;
}
```
正在开发的项目：
C语言及C++篇：
1、工资管理系统（已停止开发，见仓库）
仓库网址如下：
```
https://github.com/lichenyichay/Payroll-system-C
```
声明及结构体定义部分如下：
```C
//如下为函数声明
void gotoxy(int x, int y);//使光标移动到固定坐标
void printheader();//打印表头信息
void printdata(ZGGZ pp);//打印记录信息
void Disp(ZGGZ tp[], int n);//显示tp数组中存储的n条记录
float numberinput(const char* notice);//输入数字并验证长度
void stringinput(char* t, int lens, const char* notice);//输入字符串并验证长度
int Locate(ZGGZ tp[], int n, char findmess[], const char nameornum[]);//定位数组中符合要求的元素，并返回下标值
int Add(ZGGZ tp[], int n);//增加工资记录，并返回当前数组中的当前记录数
void Qur(ZGGZ tp[], int n);//查找满足条件的记录，并显示
int Del(ZGGZ tp[], int n);//查找满足条件的记录，并删除
void Modify(ZGGZ tp[], int n);//修改工资记录
int Insert(ZGGZ tp[], int n);//插入工资记录，并返回数组中的当前记录数
void Tongji(ZGGZ tp[], int n);//统计职工工资的整体分布情况
void Sort(ZGGZ tp[], int n);//按实发工资字段降序排序
void Save(ZGGZ tp[], int n);//写入磁盘数据文件
void menu();//显示主菜单
void Wrong();//显示错误信息
void Nofind();//显示未查找到职工信息
//如下为结构体定义
typedef struct employee {
	char num[10];//编号 
	char name[15];//姓名 
	float jbgz;//基本工资 
	float jj;//奖金 
	float kk;//扣款 
	float yfgz;//应发工资 
	float sk;//税款 
	float sfgz;//实发工资 
}ZGGZ;//定义职工的数据结构
```
2、俄罗斯方块（C语言版）（暂未开发，见仓库）
仓库网址如下：
```
https://github.com/lichenyichay/Tetris-C
```
3、俄罗斯方块（Python版）（正在开发，见仓库）
仓库网址如下：
```
https://github.com/lichenyichay/Tetris-Python
```
Android及Kotlin篇：
1、PermissionX安卓库（见仓库）
仓库网址如下：
```
https://github.com/lichenyichay/PermissionX2
```
2、电子拍卖系统（Kotlin版）（见仓库）
仓库网址如下：
```
https://github.com/lichenyichay/Electronic-auction-system-Kotlin-
```
部分代码如下：
```PHP
<?php
$arr = array(
    'code' => '200',
    'msg' => '成功',
    'data' => array(
        'id' => '1',
        'name' => 'Kotlin'
    )
);
$json_string = json_string($arr);
echo $json_string;
```
