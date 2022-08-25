Hi there 👋

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
我会的编程语言：Python、C++、C语言、Html和Java（会一丢丢）。
我的学而思编程社区主页：https://code.xueersi.com/space/13438784
我的小码王编程社区主页：https://world.xiaomawang.com/w/person/project/all/3146479
我的网易卡搭社区主页：https://kada.163.com/u/4585208.htm
我的GitHub主页：https://github.com/lichenyichay
以下是我写的部分作品：
Python集：
1、多功能一体机1.4.0（仅在学而思社区有效，持续更新）
```python
import xes.AIspeak,xes.ext,xes.weather,xes.map,xes.provinces,xes.sms,xes.word,random,time,os
from threading import Thread
i= -1
while True:
    i = i+1
    a = input("请输入你要什么服务：")
    if a == "大小写互换":
        gongneng1 = input("请输入服务：（可选项：大写转小写，小写转大写）")
        if gongneng1 == "大写转小写":
            zifugeshu = int(input("请输入字符个数"))
            if zifugeshu > 1:
                for i in range(zifugeshu):
                    zifu = input("请输入第" + (i + 1) + "个字符")
                    zifu1 = ord(zifu)
                    zifu1 = zifu1 + 32
                    zifu1 = chr(zifu1)
                    zongzifu = []
                    zongzifu.append(zifu1)
                print("转换结果：")
                for j in zongzifu:
                    print(j)
            else:
                zifu = input("请输入字符：")
                zifu1 = ord(zifu)
                zifu1 = zifu1 + 32
                zifu1 = chr(zifu1)
            print("转换结果：" + zifu1)
        elif gongneng1 == "小写转大写":
            zifugeshu = int(input("请输入字符个数"))
            if zifugeshu > 1:
                for i in range(zifugeshu):
                    zifu = input("请输入第" + (i + 1) + "个字符")
                    zifu1 = ord(zifu)
                    zifu1 = zifu1 - 32
                    zifu1 = chr(zifu1)
                    zongzifu = []
                    zongzifu.append(zifu1)
                print("转换结果：")
                for j in zongzifu:
                    print(j)
        else:
            zifu = input("请输入字符：")
            zifu1 = ord(zifu)
            zifu1 = zifu1 - 32
            zifu1 = chr(zifu1)
            print("转换结果：" + zifu1)
        print("--------------------")
    elif a == "翻译":
        b = input("请输入你要翻译的内容：")
        xes.AIspeak.speak(translate(b))
        print("--------------------")
    elif a == "调整说话速度":
        b = int(input("请输入0-2之间的数字（1是原速）："))
        xes.AIspeak.setspeed(b)
        print("现在语速为",b)
        print("--------------------")
    elif a == "调整说话语色":
        b = input("请输入语色（在boy和girl中选择）：")
        xes.AIspeak.setmode(b)
        print("--------------------")
    elif a == "发短信":
        b = input("请输入电话号码：")
        c = input("请输入发短信的内容：")
        xes.sms.send_msg(b,c)
        print("--------------------")
    elif a == "查天气":
        b = input("请输入你要查询天气的城市：")
        c = int(input("请输入索引（0:当天，1：明天，-1：昨天）"))
        d = xes.weather.air_temp(b,c)
        if b == 0:
            e = "今天" + b + d +"度"
            xes.AIspeak.speak(str(e))
            print(e)
        elif b == 1:
            e = "明天" + b + d +"度"
            xes.AIspeak.speak(str(e))
            print(e)
        elif b == -1:
            e = "昨天" + b + d +"度"
            xes.AIspeak.speak(str(e))
            print(e)
        print("--------------------")
    elif a == "查风速":
        b = input("请输入城市：")
        c = int(input("请输入索引（0:当天，1：明天，-1：昨天）"))
        d = air_speed(b,c)
        if b == 0:
            e = "今天" + b + "风速是" + d
            xes.AIspeak.speak(str(e))
            print(e)
        elif b == 1:
            e = "明天" + b + "风速是" + d
            xes.AIspeak.speak(str(e))
            print(e)
        elif b == -1:
            e = "昨天" + b + "风速是" + d
            xes.AIspeak.speak(str(e))
            print(e)
        print("--------------------")
    elif a == "查路线":
        b = input("请输入起点：")
        c = input("请输入终点：")
        d = input("请输入城市：")
        e = get_routes(b,c,d)
        print(e)
        print("--------------------")
    elif a == "查站点" and i > 1:
        b = input("请输入起点：")
        c = input("请输入终点：")
        d = input("请输入城市：")
        e = input("请输入索引：")
        f = get_routes(b,c,d)
        g = get_sites(f,e)
        h = "站点为" + g
        print(h)
        print("--------------------")
    elif a == "随机获取生僻词":
        b = xes.word.shengpici()
        xes.AIspeak.speak(b)
        print(b)
        print("--------------------")
    elif a == "随机获取生僻字":
        b = xes.word.shengpizi()
        xes.AIspeak.speak(b)
        print(b)
        print("--------------------")
    elif a == "获取拼音":
        b = input("请输入1个汉字")
        c = pinyin(b)
        xes.AIspeak.speak(c)
        print(c)
        print("--------------------")
    elif a == "判断成语":
        b = input("请输入判断的成语：")
        c = xes.word.is_idiom(b)
        if c == "y":
            d = "是成语"
            xes.AIspeak.speak(d)
            print(d)
        else:
            d = "不是成语"
            xes.AIspeak.speak(d)
            print(d)
        print("--------------------")
    elif a == "抽取随机数":
        try:
            d = int(input("请输入随机数为几进制（2或8或10或16）："))
            c = int(input("请输入最大值（整数（十进制））："))
            b = random.randint(0,c)
            if d == 2:
                b = bin(b)
            elif d == 8:
                b = oct(b)
            elif d == 10:
                b = int(b)
            elif d == 16:
                b = hex(b)
            else:
                print("不支持转换！")
            print(b)
        except Exception as e:
            print("错误信息：" + repr(e))
        print("--------------------")
    elif a == "求最小公倍数":
        num1 = int(input())
        num2 = int(input())
        for i in range(max(num1,num2),num1*num2 + 1):
            if i % num1 == 0 and i % num2 == 0:
                print(i)
                break
        print("--------------------")
    elif a == "快速排列":
        try:
            input_ = []
            answer = []
            jobs = []

            def fast_arrangement(num):
                sleep(num / 10000)
                answer.append(num)
    
            times = int(input("你要输入几个数："))
            for i in range(times):
                num = int(input("请输入数字:"))
                input_.append(num)

            for i in range(len(input_)):
                t = Thread(target=fast_arrangement, args = (input_[i],))
                jobs.append(t)
                t.start()
    
            for job in jobs:
                job.join()

            print(answer)
        except Exception as e:
            print("错误信息：" + repr(e))
        print("--------------------")
    elif a == "图形计算器":
        def tuxing():
            while True:
                huida = input("请输入计算对象：")
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
                    huida1 = input("请输入要计算的是面积还是周长：")
                    huida2 = float(input("请输入半径："))
                    if huida1 == "面积":
                        shuchu = 3.14*(huida2**2)
                        print(f"面积是：{shuchu}")
                    elif huida1 == "周长":
                        shuchu = 2*3.14*huida2
                        print(f"周长是：{shuchu}")
                    else:
                        print("不支持此功能！")
                else:
                    print("暂不支持此图形的计算！！！")
                    print("退出中......")
                    time.sleep(2)
                    break
            return 0
        tuxing()
        print("--------------------")
    elif a == "小学学生信息管理系统":
        print("这里是xx小学学生信息管理系统")
        stu = { "老八"  : "老八,岁数不明,男,厕所深处 爱好:在厕所干饭"}
        print("你可以查到所有学员的个人信息,但也请不要向外泄露")
        while True:
            print("以下是现有学员名单：")
            for k in stu:
                print(k)
            ans = input("查询学员信息请按1,删除学员信息请按2,新增学员信息请按3,退出请按0：")
            if ans == "1":
                try:
                    a = input("请输入学员姓名：")
                    print(f"{a}的相关信息是：{stu[a]}")
                    time.sleep(5)
                    print("--------------------")
                except:
                    print("无此学生")
                    time.sleep(5)
                    print("--------------------")
            elif ans == "2":
                a = input("请输入要删除的学员姓名：")
                del stu[a]
                print(a,"的相关信息已经删除")
                time.sleep(5)
                print("--------------------")
            elif ans == "3":
                a = input("请输入要添加的学员姓名：")
                b = input("请输入新增的学员信息：")
                stu[a] = b
                print(a,"的相关信息已添加")
                time.sleep(5)
                print("--------------------")
            elif ans == "0":
                print("感谢你的使用！再见")
                break
            else:
                print("无此功能")
                time.sleep(5)
        print("--------------------")
    elif a == "二分查找":
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
                time.sleep(5)
                print("--------------------")
            elif d == "no":
                print("程序结束运行！")
                break
            else:
                print("指令无效！")
        
    else:
        jieshulist = ["功能无效！","无法实现服务！","暂时还在开发！"]
        b = random.choice(jieshulist)
        xes.AIspeak.speak(b)
        print(b)
        break
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
