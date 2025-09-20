<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>C# 学习笔记 - 深入浅出</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f8f9fa;
        }
        h1 {
            color: #68217a;
            text-align: center;
            border-bottom: 2px solid #68217a;
            padding-bottom: 10px;
        }
        h2 {
            color: #68217a;
            margin-top: 30px;
            padding-bottom: 5px;
            border-bottom: 1px solid #ccc;
        }
        h3 {
            color: #501c61;
            margin-top: 20px;
        }
        code {
            background-color: #f4f4f4;
            padding: 2px 5px;
            border-radius: 3px;
            font-family: 'Cascadia Code', Consolas, monospace;
            font-size: 0.95em;
        }
        pre {
            background-color: #f4f4f4;
            padding: 15px;
            border-radius: 5px;
            overflow-x: auto;
            border-left: 4px solid #68217a;
            font-size: 0.9em;
            line-height: 1.4;
            position: relative;
        }
        ul {
            padding-left: 20px;
        }
        li {
            margin-bottom: 8px;
        }
        .note {
            background-color: #e7f3fe;
            border-left: 4px solid #2196F3;
            padding: 15px;
            margin: 15px 0;
            border-radius: 0 5px 5px 0;
        }
        .container {
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
        }
        .header {
            text-align: center;
            margin-bottom: 30px;
        }
        .chapter {
            counter-increment: chapter;
        }
        .chapter::before {
            content: counter(chapter) ". ";
        }
        .analogy {
            background-color: #fff4e6;
            border-left: 4px solid #ff922b;
            padding: 15px;
            margin: 15px 0;
            border-radius: 0 5px 5px 0;
        }
        .key-concept {
            background-color: #e6f7ff;
            padding: 10px 15px;
            border-radius: 5px;
            margin: 10px 0;
            border-left: 4px solid #1890ff;
        }
        .toc {
            background-color: #f0e6ff;
            padding: 20px;
            border-radius: 8px;
            margin-bottom: 30px;
        }
        .toc h2 {
            margin-top: 0;
            color: #501c61;
        }
        .toc ul {
            columns: 2;
            padding-left: 20px;
        }
        .toc li {
            margin-bottom: 8px;
            break-inside: avoid;
        }
        .toc a {
            text-decoration: none;
            color: #501c61;
        }
        .toc a:hover {
            text-decoration: underline;
            color: #68217a;
        }
        .copy-btn {
            position: absolute;
            top: 5px;
            right: 5px;
            background: #68217a;
            color: white;
            border: none;
            border-radius: 3px;
            padding: 5px 10px;
            cursor: pointer;
            font-size: 12px;
            opacity: 0.8;
            transition: opacity 0.3s;
        }
        .copy-btn:hover {
            opacity: 1;
        }
        .code-container {
            position: relative;
        }
        .code-header {
            background: #68217a;
            color: white;
            padding: 5px 10px;
            border-radius: 5px 5px 0 0;
            font-family: 'Cascadia Code', Consolas, monospace;
            font-size: 0.9em;
            display: inline-block;
            margin-bottom: -10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>C# 学习笔记 - 深入浅出</h1>
        </div>

        <!-- 添加目录 -->
        <div class="toc">
            <h2>目录</h2>
            <ul>
                <li><a href="#section1">1. C# 与 .NET 概述</a></li>
                <li><a href="#section2">2. 开发环境配置</a></li>
                <li><a href="#section3">3. 第一个C#程序与程序结构</a></li>
                <li><a href="#section4">4. C# 关键字与注释</a></li>
                <li><a href="#section5">5. 数据类型与变量</a></li>
                <li><a href="#section6">6. 数据类型转换</a></li>
                <li><a href="#section7">7. 运算符与优先级</a></li>
                <li><a href="#section8">8. 常量与只读变量</a></li>
                <li><a href="#section9">9. 流程控制：条件与分支</a></li>
                <li><a href="#section10">10. 流程控制：循环结构</a></li>
                <li><a href="#section11">11. 函数（方法）的定义与使用</a></li>
                <li><a href="#section12">12. 面向对象基础：类与封装</a></li>
                <li><a href="#section13">13. 参数传递方式</a></li>
                <li><a href="#section14">14. 可空类型</a></li>
                <li><a href="#section15">15. 数组</a></li>
                <li><a href="#section16">16. 参数数组与Array类</a></li>
                <li><a href="#section17">17. 字符串操作</a></li>
                <li><a href="#section18">18. 结构体与枚举</a></li>
                <li><a href="#section19">19. 类与对象</a></li>
                <li><a href="#section20">20. 构造函数与析构函数</a></li>
                <li><a href="#section21">21. 总结与后续学习方向</a></li>
            </ul>
        </div>

        <h2 id="section1">1. C# 与 .NET 概述</h2>
        <p>C#（读作"C Sharp"）是由微软开发的一种面向对象的编程语言，运行在.NET平台上。它结合了C++的强大功能和Visual Basic的简易性。</p>
        
        <h3>.NET框架</h3>
        <p>.NET是一个跨语言的开发平台，提供了庞大的类库（Framework Class Library）和公共语言运行时（Common Language Runtime）。</p>
        
        <h3>C#的历史与版本</h3>
        <p>C#于千禧年首次亮相，至今已经迭代多个版本，每个版本都引入了新特性，如异步编程、模式匹配、记录类型等。</p>
        
        <h3>C#的应用领域</h3>
        <ul>
            <li>Windows桌面应用（WinForms、WPF）</li>
            <li>Web应用（ASP.NET Core）</li>
            <li>游戏开发（Unity3D、GodotEngine）</li>
            <li>移动应用（Xamarin）</li>
            <li>云计算和微服务</li>
        </ul>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 把C#想象成一种多功能工具套装（像瑞士军刀），而.NET则是这个工具套装的工作台。工作台(.NET)提供了所有的基础设施和工作空间，而C#则是其中最强大、最灵活的工具之一。你可以用这套工具建造从小木屋(简单应用)到摩天大楼(复杂系统)的各种项目。</p>
        </div>

        <h2 id="section2">2. 开发环境配置</h2>
        <p>推荐使用以下工具进行C#开发：</p>
        <ul>
            <li><strong>Visual Studio</strong>：功能强大的IDE，适合Windows开发，提供完整的开发体验</li>
            <li><strong>Visual Studio Code</strong>：轻量级，跨平台，配合C#扩展和.NET SDK使用</li>
            <li><strong>JetBrains Rider</strong>：跨平台的.NET IDE，功能强大</li>
        </ul>
        
        <div class="note">
            <p><strong>提示：</strong> 对于初学者，推荐使用Visual Studio Community版，它免费且功能齐全。</p>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 选择开发工具就像选择厨房设备。Visual Studio是一个功能齐全的"智能厨房"，有自动切菜机、智能烤箱等一切设备；VS Code像一个高品质的"厨师刀套装"，轻便但功能强大；Rider则像一个专业厨房，为高级厨师设计。初学者最好从"智能厨房"开始，等熟悉了再尝试其他工具。</p>
        </div>

        <h2 id="section3">3. 第一个C#程序与程序结构</h2>
        <p>下面是一个最简单的C#程序：</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>C#程序的基本结构</h3>
        <ul>
            <li><strong>引用命名空间</strong>：<code>using System;</code></li>
            <li><strong>命名空间声明</strong>：<code>namespace HelloWorld {...}</code></li>
            <li><strong>类声明</strong>：<code>class Program {...}</code></li>
            <li><strong>Main方法</strong>：程序的入口点<code>static void Main(string[] args) {...}</code></li>
            <li><strong>语句</strong>：执行具体操作的代码<code>Console.WriteLine("Hello World!");</code></li>
        </ul>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 编写C#程序就像写一封信。命名空间是信封上的地址，确保信能送到正确的地方；类是信纸本身；Main方法是信的开头"亲爱的..."；语句则是信的具体内容。没有正确地址的信可能送错地方，没有Main方法的程序计算机不知道从哪里开始执行。</p>
        </div>

        <h2 id="section4">4. C# 关键字与注释</h2>
        <h3>C#关键字</h3>
        <p>C#关键字是语言预留的具有特殊意义的单词，不能用作标识符（变量名、类名等）。</p>
        <p>常见关键字：<code>using</code>, <code>namespace</code>, <code>class</code>, <code>static</code>, <code>void</code>, <code>if</code>, <code>for</code>, <code>int</code>, <code>double</code>等。</p>
        
        <h3>注释</h3>
        <p>注释是写给程序员看的说明文字，编译器会忽略它们。</p>
        <ul>
            <li><strong>单行注释</strong>：<code>// 这是单行注释</code></li>
            <li><strong>多行注释</strong>：<code>/* 这是多行注释 */</code></li>
            <li><strong>XML文档注释</strong>：<code>/// <summary>XML文档注释</summary></code></li>
        </ul>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 关键字就像是交通规则中的专用标志（如"停止"、"让行"），你不能把这些词用作街道名称。注释则像是给其他司机的路标或说明，比如"前方急转弯"或"此处易拥堵"，它们不影响道路本身，但能帮助他人更好地理解路况。</p>
        </div>

        <h2 id="section5">5. 数据类型与变量</h2>
        <h3>基本数据类型</h3>
        <ul>
            <li><code>int</code>：整型（32位有符号整数）</li>
            <li><code>double</code>：双精度浮点型</li>
            <li><code>float</code>：单精度浮点型</li>
            <li><code>decimal</code>：高精度十进制数，适合金融计算</li>
            <li><code>bool</code>：布尔值（true或false）</li>
            <li><code>char</code>：字符型</li>
            <li><code>string</code>：字符串</li>
        </ul>
        
        <h3>变量</h3>
        <p>变量是存储数据的容器，需要先声明后使用。</p>
        <p>声明变量的语法：<code>数据类型 变量名;</code></p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class VariableExample
{
    static void Main()
    {
        int age; // 声明变量
        age = 25; // 赋值
        string name = "北海岸冰"; // 声明并初始化
        var message = "exyone"; // 使用var关键字，编译器推断类型
        
        Console.WriteLine($"姓名: {name}, 年龄: {age}, 消息: {message}");
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 变量就像不同大小的储物盒。int是小型收纳盒，适合放小物件；double和float是不同精度的量杯；decimal是精密的药剂瓶；bool是开关（只有开/关两种状态）；char是字母磁贴；string则是可以放很多字母磁贴的长条磁板。给变量赋值就像往盒子里放东西，必须先确定盒子类型（数据类型）和贴上标签（变量名）。</p>
        </div>

        <h2 id="section6">6. 数据类型转换</h2>
        <h3>隐式转换</h3>
        <p>小范围类型向大范围类型自动转换，不会丢失数据。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class ConversionExample
{
    static void Main()
    {
        int num = 10;
        double bigNum = num; // 自动转换为double
        
        Console.WriteLine($"整型: {num}, 转换后的双精度型: {bigNum}");
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>显式转换</h3>
        <p>大范围类型向小范围类型强制转换，可能丢失数据。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class ExplicitConversionExample
{
    static void Main()
    {
        double bigNum = 10.5;
        int num = (int)bigNum; // 强制转换为int，结果为10
        
        Console.WriteLine($"双精度型: {bigNum}, 强制转换后的整型: {num}");
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>使用Convert类和方法</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class ConvertExample
{
    static void Main()
    {
        string str = "123";
        int num = Convert.ToInt32(str); // 转换为int
        double d = double.Parse("3.14"); // 使用Parse方法
        
        Console.WriteLine($"字符串 '{str}' 转换为整型: {num}");
        Console.WriteLine($"字符串 '3.14' 转换为双精度型: {d}");
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 数据类型转换就像在不同容器间倒水。隐式转换是小杯水倒进大杯，不会洒出；显式转换是大杯水倒进小杯，可能溢出(数据丢失)；Convert类和方法则像使用量杯和漏斗，有专门的工具帮助转换，更加安全可控。</p>
        </div>

        <h2 id="section7">7. 运算符与优先级</h2>
        <h3>算术运算符</h3>
        <p><code>+</code>（加）, <code>-</code>（减）, <code>*</code>（乘）, <code>/</code>（除）, <code>%</code>（取余）</p>
        
        <h3>赋值运算符</h3>
        <p><code>=</code>, <code>+=</code>, <code>-=</code>, <code>*=</code>, <code>/=</code>, <code>%=</code></p>
        
        <h3>比较运算符</h3>
        <p><code>==</code>, <code>!=</code>, <code>&gt;</code>, <code>&lt;</code>, <code>&gt;=</code>, <code>&lt;=</code></p>
        
        <h3>逻辑运算符</h3>
        <p><code>&amp;&amp;</code>（与）, <code>||</code>（或）, <code>!</code>（非）</p>
        
        <h3>运算符优先级</h3>
        <p>从高到低：括号 > 算术运算符 > 比较运算符 > 逻辑运算符 > 赋值运算符</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class OperatorExample
{
    static void Main()
    {
        // 算术运算符
        int a = 10 + 5;  // 15
        int b = 10 - 5;  // 5
        int c = 10 * 5;  // 50
        int d = 10 / 5;  // 2
        int e = 10 % 3;  // 1
        
        Console.WriteLine($"算术运算: 10+5={a}, 10-5={b}, 10*5={c}, 10/5={d}, 10%3={e}");
        
        // 赋值运算符
        int x = 10;
        x += 5;  // x = 15
        Console.WriteLine($"赋值运算: x += 5 → {x}");
        
        // 比较运算符
        bool result1 = (10 > 5);   // true
        bool result2 = (10 == 5);  // false
        Console.WriteLine($"比较运算: 10>5={result1}, 10==5={result2}");
        
        // 逻辑运算符
        bool result3 = (true && false); // false
        bool result4 = (true || false); // true
        bool result5 = !true;           // false
        Console.WriteLine($"逻辑运算: true&&false={result3}, true||false={result4}, !true={result5}");
        
        // 优先级示例
        int result6 = 2 + 3 * 4;     // 14 (乘法优先)
        int result7 = (2 + 3) * 4;   // 20 (括号优先)
        Console.WriteLine($"优先级: 2+3*4={result6}, (2+3)*4={result7}");
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <div class="note">
            <p><strong>提示：</strong> 当不确定优先级时，使用括号可以明确运算顺序。</p>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 运算符优先级就像数学运算规则。乘除法优先于加减法，括号内的运算最优先。这就像在超市结账：会员折扣(括号)最先计算，然后是买一送一活动(乘除)，最后是普通商品价格(加减)。不了解优先级规则就像不按顺序扫描商品，会得到错误的总价。</p>
        </div>

        <h2 id="section8">8. 常量与只读变量</h2>
        <h3>常量（const）</h3>
        <p>使用<code>const</code>关键字声明，必须在声明时初始化，之后不能修改。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class ConstantExample
{
    const double Pi = 3.14159;
    const int DaysInWeek = 7;
    
    static void Main()
    {
        Console.WriteLine($"圆周率: {Pi}");
        Console.WriteLine($"一周天数: {DaysInWeek}");
        
        // 以下代码如果取消注释会报错，因为常量不能修改
        // Pi = 3.14;
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>只读变量（readonly）</h3>
        <p>使用<code>readonly</code>关键字声明，可以在声明时或构造函数中初始化，之后不能修改。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class ReadOnlyExample
{
    readonly string connectionString;
    
    public ReadOnlyExample()
    {
        connectionString = "server=localhost;database=test;";
    }
    
    static void Main()
    {
        ReadOnlyExample example = new ReadOnlyExample();
        Console.WriteLine($"连接字符串: {example.connectionString}");
        
        // 以下代码如果取消注释会报错，因为只读字段不能在方法中修改
        // example.connectionString = "new connection string";
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 常量就像刻在石头上的法律条文，一旦刻上就永远不能改变；只读变量则像用特殊墨水写在纸上的重要规定，在制定阶段(构造函数中)可以书写，但一旦制定完成并发布，就不能再修改。const适用于像圆周率这样的绝对不变的值，readonly适用于像数据库连接字符串这样在程序初始化后不再改变的值。</p>
        </div>

        <h2 id="section9">9. 流程控制：条件与分支</h2>
        <h3>if/else语句</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class ConditionExample
{
    static void Main()
    {
        Console.WriteLine("请输入您的年龄:");
        int age = Convert.ToInt32(Console.ReadLine());
        
        if (age < 0)
        {
            Console.WriteLine("年龄不能为负数!");
        }
        else if (age < 18)
        {
            Console.WriteLine("您是未成年人。");
        }
        else if (age < 60)
        {
            Console.WriteLine("您是成年人。");
        }
        else
        {
            Console.WriteLine("您是老年人。");
        }
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>switch语句</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class SwitchExample
{
    static void Main()
    {
        Console.WriteLine("请输入星期几 (1-7):");
        int day = Convert.ToInt32(Console.ReadLine());
        
        switch (day)
        {
            case 1:
                Console.WriteLine("星期一：努力工作!");
                break;
            case 2:
                Console.WriteLine("星期二：继续努力!");
                break;
            case 3:
                Console.WriteLine("星期三：一周过半!");
                break;
            case 4:
                Console.WriteLine("星期四：周末快来了!");
                break;
            case 5:
                Console.WriteLine("星期五：最后冲刺!");
                break;
            case 6:
                Console.WriteLine("星期六：休息日!");
                break;
            case 7:
                Console.WriteLine("星期日：放松一天!");
                break;
            default:
                Console.WriteLine("输入错误，请输入1-7之间的数字!");
                break;
        }
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 条件语句就像交通信号灯。if/else是普通的红绿灯，根据条件(红灯/绿灯)决定是否通行；switch语句则像多车道转盘，根据你的目的地(case值)选择正确的出口。if/else适合处理范围判断(如年龄范围)，switch适合处理具体值匹配(如星期几)。</p>
        </div>

        <h2 id="section10">10. 流程控制：循环结构</h2>
        <h3>for循环</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class ForLoopExample
{
    static void Main()
    {
        Console.WriteLine("for循环示例:");
        for (int i = 0; i < 5; i++)
        {
            Console.WriteLine($"当前计数: {i}");
        }
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>while循环</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class WhileLoopExample
{
    static void Main()
    {
        Console.WriteLine("while循环示例:");
        int count = 0;
        while (count < 5)
        {
            Console.WriteLine($"当前计数: {count}");
            count++;
        }
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>do-while循环</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class DoWhileLoopExample
{
    static void Main()
    {
        Console.WriteLine("do-while循环示例:");
        int count = 0;
        do
        {
            Console.WriteLine($"当前计数: {count}");
            count++;
        } while (count < 5);
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>foreach循环</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class ForEachLoopExample
{
    static void Main()
    {
        Console.WriteLine("foreach循环示例:");
        string[] fruits = { "苹果", "香蕉", "橙子", "葡萄" };
        
        foreach (string fruit in fruits)
        {
            Console.WriteLine($"水果: {fruit}");
        }
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>循环控制语句</h3>
        <ul>
            <li><code>break</code>：终止整个循环</li>
            <li><code>continue</code>：跳过本次循环的剩余代码，继续下一次循环</li>
        </ul>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class LoopControlExample
{
    static void Main()
    {
        Console.WriteLine("break示例:");
        for (int i = 0; i < 10; i++)
        {
            if (i == 5)
            {
                Console.WriteLine("遇到5，终止循环");
                break;
            }
            Console.WriteLine($"当前值: {i}");
        }
        
        Console.WriteLine("\ncontinue示例:");
        for (int i = 0; i < 5; i++)
        {
            if (i == 2)
            {
                Console.WriteLine("遇到2，跳过此次循环");
                continue;
            }
            Console.WriteLine($"当前值: {i}");
        }
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 循环就像工厂的生产线。for循环是知道要生产多少产品的流水线；while循环是"只要还有原材料就继续生产"的流水线；do-while是"至少生产一件产品看看效果"的流水线；foreach则是"处理篮子里的每一个水果"的流水线。break就像紧急停止按钮，完全停止生产线；continue则是跳过当前有问题的产品，继续处理下一个。</p>
        </div>

        <h2 id="section11">11. 函数（方法）的定义与使用</h2>
        <p>函数是完成特定任务的代码块，可以重复使用。你可以把函数想象成一个"做特定任务的机器"或"一个打包好的指令盒子"。</p>
        
        <div class="analogy">
            <p><strong>现实比喻：</strong> 就像冲咖啡的步骤：拿杯子、加咖啡粉、倒热水、搅拌。如果你每天都要重复，可以给这一系列步骤起个名字叫"冲咖啡"，以后只需要说"冲咖啡"就知道要执行这些动作。</p>
        </div>
        
        <h3>方法定义</h3>
        <pre><code>访问修饰符 返回类型 方法名(参数列表)
{
    // 方法体
    return 返回值; // 如果返回类型不是void
}</code></pre>
        
        <h3>方法示例</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class FunctionExample
{
    // 无参数无返回值的方法
    public static void MakeCoffee()
    {
        Console.WriteLine("1. 拿一个杯子");
        Console.WriteLine("2. 加入咖啡粉");
        Console.WriteLine("3. 倒入热水");
        Console.WriteLine("4. 搅拌一下");
        Console.WriteLine("咖啡冲好了！");
    }

    // 带参数和返回值的方法
    public static int Add(int a, int b)
    {
        return a + b;
    }

    public static void PrintMessage(string message)
    {
        Console.WriteLine(message);
    }
    
    static void Main()
    {
        // 调用方法
        MakeCoffee(); // 只需调用函数名，就会执行里面的所有代码
        
        int result = Add(5, 3); // 返回8
        Console.WriteLine($"5 + 3 = {result}");
        
        PrintMessage("Hello, World!"); // 输出Hello, World!
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <h3>参数与返回值</h3>
        <ul>
            <li><strong>参数（Parameters）</strong>：函数工作时需要的"材料"或"信息"</li>
            <li><strong>返回值（Return Value）</strong>：函数工作完成后"产出"的结果</li>
        </ul>
        
        <div class="key-concept">
            <p><strong>关键概念：</strong> 使用函数可以避免代码重复，让程序更清晰、更易维护。</p>
        </div>

        <h2 id="section12">12. 面向对象基础：类与封装</h2>
        <h3>类的定义</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

public class Person
{
    // 字段
    private string name;
    private int age;
    
    // 属性
    public string Name
    {
        get { return name; }
        set { name = value; }
    }
    
    public int Age
    {
        get { return age; }
        set { age = value; }
    }
    
    // 方法
    public void Introduce()
    {
        Console.WriteLine($"我叫{name}，今年{age}岁。");
    }
}

class ClassExample
{
    static void Main()
    {
        Person person = new Person();
        person.Name = "张三";
        person.Age = 25;
        person.Introduce();
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>封装的概念与重要性</h3>
        <p>封装是面向对象编程的基本原则之一，它将数据和行为组合在一个单元中，并控制对数据的访问。</p>
        
        <div class="analogy">
            <p><strong>现实比喻：</strong> 汽车是一个封装的好例子。内部复杂的发动机工作原理被封装在引擎盖下，暴露给你的只是方向盘、油门和刹车踏板。你不需要知道引擎原理，只需知道"踩油门车会走"。</p>
        </div>
        
        <h3>封装的好处</h3>
        <ul>
            <li><strong>安全</strong>：保护重要数据不被随意修改</li>
            <li><strong>易用</strong>：使用者只需知道函数有什么用、怎么调用，无需关心内部实现</li>
            <li><strong>易于维护</strong>：只要函数接口不变，内部实现可以任意优化修改</li>
        </ul>
        
        <h3>通过访问修饰符实现封装</h3>
        <ul>
            <li><code>public</code>：完全公开，任何代码都可以访问</li>
            <li><code>private</code>：仅类内部可访问</li>
            <li><code>protected</code>：类内部和派生类可访问</li>
            <li><code>internal</code>：同一程序集内可访问</li>
        </ul>

        <h3>封装的实际示例：银行账户</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

public class BankAccount
{
    // 私有字段：余额被"封装"起来，外部不能直接访问
    private double _balance;

    // 构造函数，初始化账户
    public BankAccount(double initialBalance)
    {
        _balance = initialBalance;
    }

    // 公开的方法：存钱，这是暴露给外部的"接口"
    public void Deposit(double amount)
    {
        if (amount > 0)
        {
            _balance += amount;
            Console.WriteLine($"存入了 {amount} 元。当前余额：{_balance}");
        }
        else
        {
            Console.WriteLine("存款金额必须大于0。");
        }
    }

    // 公开的方法：取钱（带安全检查）
    public void Withdraw(double amount)
    {
        if (amount > 0 && amount <= _balance)
        {
            _balance -= amount;
            Console.WriteLine($"取出了 {amount} 元。当前余额：{_balance}");
        }
        else
        {
            Console.WriteLine("取款失败：金额无效或余额不足。");
        }
    }

    // 公开的方法：获取当前余额（只读，不能修改）
    public double GetBalance()
    {
        return _balance;
    }
}

class EncapsulationExample
{
    static void Main()
    {
        BankAccount myAccount = new BankAccount(1000); // 开户，存1000元

        // myAccount._balance = 1000000; // 错误！_balance是private的，外部无法直接修改，保证了安全！

        myAccount.Deposit(500);    // 正确：通过公开的接口存钱
        myAccount.Withdraw(200);   // 正确：通过公开的接口取钱
        myAccount.Withdraw(2000);  // 正确：但会触发安全检查，取款失败

        double currentBalance = myAccount.GetBalance(); // 通过公开的接口查询余额
        Console.WriteLine($"最终余额：{currentBalance}");
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="key-concept">
            <p><strong>关键概念：</strong> 封装就是把数据（字段）和操作数据的函数（方法）捆绑在一起（类），并隐藏一切不必要的内部实现细节，只暴露一个安全、简洁的接口供外界使用。</p>
        </div>

        <h2 id="section13">13. 参数传递方式</h2>
        <p>C#支持三种参数传递方式：值传递、引用传递和输出传递。</p>
        
        <h3>值传递</h3>
        <p>默认的参数传递方式，传递的是变量的副本。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class ParameterPassingExample
{
    static void ModifyValue(int x)
    {
        x = 10; // 不影响原始值
        Console.WriteLine($"方法内 x 的值: {x}");
    }

    static void Main()
    {
        int num = 5;
        Console.WriteLine($"调用前 num 的值: {num}");
        
        ModifyValue(num);
        
        Console.WriteLine($"调用后 num 的值: {num}"); // 输出: 5
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>引用传递</h3>
        <p>使用<code>ref</code>关键字，传递的是变量的引用。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class RefExample
{
    static void ModifyRef(ref int x)
    {
        x = 10; // 修改原始值
        Console.WriteLine($"方法内 x 的值: {x}");
    }

    static void Main()
    {
        int num = 5;
        Console.WriteLine($"调用前 num 的值: {num}");
        
        ModifyRef(ref num);
        
        Console.WriteLine($"调用后 num 的值: {num}"); // 输出: 10
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>输出传递</h3>
        <p>使用<code>out</code>关键字，用于从方法返回多个值。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class OutExample
{
    static void Calculate(int a, int b, out int sum, out int product)
    {
        sum = a + b;
        product = a * b;
    }

    static void Main()
    {
        int s, p;
        Calculate(3, 4, out s, out p);
        Console.WriteLine($"Sum: {s}, Product: {p}"); // 输出: Sum: 7, Product: 12
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 参数传递方式就像不同的文件共享方式。值传递像是给对方一份文件复印件，对方可以随意修改复印件，但不影响你的原件；引用传递像是给对方一个共享文档链接，对方对文档的任何修改你都能看到；输出传递则像是让对方填写你提供的表格，你提供空白表格(out参数)，对方填写后返还给你。</p>
        </div>

        <h2 id="section14">14. 可空类型</h2>
        <p>可空类型允许值类型具有<code>null</code>值，使用<code>?</code>后缀声明。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class NullableExample
{
    static void Main()
    {
        int? nullableInt = null;
        double? nullableDouble = 3.14;

        Console.WriteLine($"nullableInt 有值吗? {nullableInt.HasValue}");
        Console.WriteLine($"nullableDouble 有值吗? {nullableDouble.HasValue}");

        if (nullableInt.HasValue)
        {
            Console.WriteLine($"nullableInt 的值: {nullableInt.Value}");
        }
        else
        {
            Console.WriteLine("nullableInt 的值为 null");
        }

        // 空合并运算符 ??
        int actualValue = nullableInt ?? 0; // 如果nullableInt为null，则返回0
        Console.WriteLine($"actualValue 的值: {actualValue}");
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 可空类型就像一个有/无物品的盒子。普通值类型盒子必须放东西，而可空类型盒子可以空着(null)。HasValue属性检查盒子里是否有东西，??运算符则提供"如果盒子是空的，就用这个默认值"的功能。这在处理数据库记录或用户输入时特别有用，因为这些数据可能缺失。</p>
        </div>

        <h2 id="section15">15. 数组</h2>
        <p>数组是存储相同类型元素的固定大小的顺序集合。</p>
        
        <h3>一维数组</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class ArrayExample
{
    static void Main()
    {
        // 声明和初始化数组
        int[] numbers = new int[5]; // 5个元素的数组
        int[] numbers2 = { 1, 2, 3, 4, 5 }; // 声明并初始化

        // 访问数组元素
        numbers[0] = 10;
        int first = numbers[0];
        Console.WriteLine($"numbers[0] = {first}");

        // 遍历数组
        Console.WriteLine("numbers2 数组元素:");
        foreach (int num in numbers2)
        {
            Console.WriteLine(num);
        }
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>多维数组</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class MultiDimensionalArrayExample
{
    static void Main()
    {
        // 二维数组
        int[,] matrix = new int[3, 4]; // 3行4列
        int[,] matrix2 = { {1, 2, 3}, {4, 5, 6} }; // 2行3列

        // 访问元素
        matrix[1, 2] = 10;
        int value = matrix[1, 2];
        Console.WriteLine($"matrix[1, 2] = {value}");

        // 遍历多维数组
        Console.WriteLine("matrix2 数组元素:");
        for (int i = 0; i < matrix2.GetLength(0); i++)
        {
            for (int j = 0; j < matrix2.GetLength(1); j++)
            {
                Console.Write(matrix2[i, j] + " ");
            }
            Console.WriteLine();
        }
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>交错数组</h3>
        <p>交错数组是数组的数组，每个子数组可以有不同长度。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class JaggedArrayExample
{
    static void Main()
    {
        // 声明交错数组
        int[][] jaggedArray = new int[3][];

        // 初始化子数组
        jaggedArray[0] = new int[] { 1, 2, 3 };
        jaggedArray[1] = new int[] { 4, 5 };
        jaggedArray[2] = new int[] { 6, 7, 8, 9 };

        // 访问元素
        int element = jaggedArray[0][1]; // 值为2
        Console.WriteLine($"jaggedArray[0][1] = {element}");

        // 遍历交错数组
        Console.WriteLine("交错数组元素:");
        for (int i = 0; i < jaggedArray.Length; i++)
        {
            Console.Write($"第{i}行: ");
            for (int j = 0; j < jaggedArray[i].Length; j++)
            {
                Console.Write(jaggedArray[i][j] + " ");
            }
            Console.WriteLine();
        }
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 数组就像一排邮箱或储物柜。一维数组是一排邮箱，每个邮箱有一个编号(索引)；多维数组像大楼里的邮箱矩阵，需要楼层和房间号两个坐标才能定位；交错数组则像不同大小的储物柜组合，每排储物柜的大小可以不同。数组让你可以用一个名字管理多个相同类型的值，并通过索引快速访问。</p>
        </div>

        <h2 id="section16">16. 参数数组与Array类</h2>
        
        <h3>参数数组</h3>
        <p>使用<code>params</code>关键字允许方法接受可变数量的参数。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class ParamsExample
{
    public static int Sum(params int[] numbers)
    {
        int total = 0;
        foreach (int num in numbers)
        {
            total += num;
        }
        return total;
    }

    static void Main()
    {
        // 调用方式
        int result1 = Sum(1, 2, 3); // 返回6
        int result2 = Sum(1, 2, 3, 4, 5); // 返回15
        int result3 = Sum(); // 返回0
        
        Console.WriteLine($"Sum(1, 2, 3) = {result1}");
        Console.WriteLine($"Sum(1, 2, 3, 4, 5) = {result2}");
        Console.WriteLine($"Sum() = {result3}");
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>Array类</h3>
        <p>System.Array类提供了许多有用的静态方法操作数组。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

class ArrayClassExample
{
    static void Main()
    {
        int[] numbers = { 5, 3, 8, 1, 9 };

        Console.Write("原始数组: ");
        PrintArray(numbers);

        // 排序
        Array.Sort(numbers); // 结果: 1, 3, 5, 8, 9
        Console.Write("排序后: ");
        PrintArray(numbers);

        // 反转
        Array.Reverse(numbers); // 结果: 9, 8, 5, 3, 1
        Console.Write("反转后: ");
        PrintArray(numbers);

        // 查找元素
        int index = Array.IndexOf(numbers, 5); // 返回2
        Console.WriteLine($"数字5的索引: {index}");

        // 复制数组
        int[] copy = new int[numbers.Length];
        Array.Copy(numbers, copy, numbers.Length);
        Console.Write("复制后的数组: ");
        PrintArray(copy);
    }

    static void PrintArray(int[] arr)
    {
        foreach (int num in arr)
        {
            Console.Write(num + " ");
        }
        Console.WriteLine();
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> params参数就像自助餐厅的"任选几种菜"选项，你可以选3样、5样或任意数量的菜，餐厅(方法)都会处理。Array类则像是一个多功能厨房工具集，提供切菜(排序)、翻转(反转)、查找特定食材(IndexOf)、复制菜品(复制数组)等各种功能，让你更高效地处理食材(数组数据)。</p>
        </div>

        <h2 id="section17">17. 字符串操作</h2>
        <p>字符串是Unicode字符的不可变序列，使用System.String类表示。</p>
        
        <h3>字符串常用操作</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;
using System.Text;

class StringExample
{
    static void Main()
    {
        string str1 = "Hello";
        string str2 = "World";

        // 连接字符串
        string combined = str1 + " " + str2; // "Hello World"
        string formatted = string.Format("{0} {1}", str1, str2); // "Hello World"

        // 字符串插值 (C# 6.0+)
        string interpolated = $"{str1} {str2}"; // "Hello World"

        Console.WriteLine($"连接后的字符串: {combined}");
        Console.WriteLine($"格式化的字符串: {formatted}");
        Console.WriteLine($"插值的字符串: {interpolated}");

        // 常用方法
        int length = combined.Length; // 11
        string upper = combined.ToUpper(); // "HELLO WORLD"
        bool contains = combined.Contains("Hello"); // true
        string substring = combined.Substring(6, 5); // "World"

        Console.WriteLine($"字符串长度: {length}");
        Console.WriteLine($"大写: {upper}");
        Console.WriteLine($"包含'Hello': {contains}");
        Console.WriteLine($"子字符串(6,5): {substring}");

        // 分割字符串
        string[] words = "C# is awesome".Split(' ');
        Console.WriteLine("分割后的单词:");
        foreach (string word in words)
        {
            Console.WriteLine(word);
        }

        // 字符串构建 (适用于大量字符串操作)
        StringBuilder sb = new StringBuilder();
        sb.Append("Hello");
        sb.Append(" ");
        sb.Append("World");
        string result = sb.ToString(); // "Hello World"
        Console.WriteLine($"StringBuilder 结果: {result}");
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 字符串操作就像处理文本段落。连接字符串像把两个句子连成一段；分割字符串像把段落拆分成单个句子；ToUpper()像把文本全部大写；Substring()像从文章中摘录一段。StringBuilder则像是一个可重复使用的写字板，可以不断添加内容，最后一次性转换成完整的字符串，比频繁修改字符串本身更高效。</p>
        </div>

        <h2 id="section18">18. 结构体与枚举</h2>
        
        <h3>结构体</h3>
        <p>结构体是值类型，适用于小型数据结构。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

public struct Point
{
    public int X;
    public int Y;
    
    public Point(int x, int y)
    {
        X = x;
        Y = y;
    }
    
    public void Display()
    {
        Console.WriteLine($"({X}, {Y})");
    }
}

class StructExample
{
    static void Main()
    {
        // 使用结构体
        Point p = new Point(10, 20);
        p.Display(); // 输出: (10, 20)
        
        // 结构体是值类型
        Point p2 = p;
        p2.X = 30;
        
        Console.Write("p: ");
        p.Display(); // 输出: (10, 20) - 原始值未改变
        Console.Write("p2: ");
        p2.Display(); // 输出: (30, 20)
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>枚举</h3>
        <p>枚举是一组命名常量的集合。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

public enum Days
{
    Sunday,    // 0
    Monday,    // 1
    Tuesday,   // 2
    Wednesday, // 3
    Thursday,  // 4
    Friday,    // 5
    Saturday   // 6
}

public enum Status : byte
{
    Inactive = 0,
    Active = 1,
    Pending = 2
}

class EnumExample
{
    static void Main()
    {
        // 使用枚举
        Days today = Days.Wednesday;
        Console.WriteLine(today); // 输出: Wednesday

        // 获取枚举值
        int dayValue = (int)Days.Friday; // 5
        Console.WriteLine($"Friday 的值: {dayValue}");

        // 从值获取枚举
        Days day = (Days)3; // Wednesday
        Console.WriteLine($"值3对应的枚举: {day}");

        // 使用自定义基类型的枚举
        Status currentStatus = Status.Active;
        byte statusValue = (byte)currentStatus; // 1
        Console.WriteLine($"当前状态: {currentStatus}, 值: {statusValue}");
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 结构体就像一个小型快递包裹，包含几个相关的数据项(如长宽高重量)，整个包裹可以方便地传递。枚举则像是一组预设的选项按钮，比如"订单状态"可以有"已下单、已发货、已完成"等选项，使用枚举比使用神秘数字代码(0,1,2)更清晰易懂。</p>
        </div>

        <h2 id="section19">19. 类与对象</h2>
        <p>类是面向对象编程的基本构建块，包含数据成员和函数成员。</p>
        
        <h3>类的基本结构</h3>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

public class Car
{
    // 字段
    private string brand;
    private int speed;
    
    // 属性
    public string Brand
    {
        get { return brand; }
        set { brand = value; }
    }
    
    public int Speed
    {
        get { return speed; }
        set { speed = value; }
    }
    
    // 自动属性
    public string Color { get; set; }
    
    // 构造函数
    public Car(string brand, string color)
    {
        Brand = brand;
        Color = color;
        Speed = 0;
    }
    
    // 方法
    public void Accelerate(int increment)
    {
        Speed += increment;
        Console.WriteLine($"加速 {increment} km/h");
    }
    
    public void Brake(int decrement)
    {
        Speed = Math.Max(0, Speed - decrement);
        Console.WriteLine($"减速 {decrement} km/h");
    }
    
    public void DisplayInfo()
    {
        Console.WriteLine($"{Brand}汽车, 颜色: {Color}, 当前速度: {Speed} km/h");
    }
}

class ClassObjectExample
{
    static void Main()
    {
        // 使用类创建对象
        Car myCar = new Car("Toyota", "Red");
        myCar.DisplayInfo();
        
        myCar.Accelerate(50);
        myCar.DisplayInfo();
        
        myCar.Brake(20);
        myCar.DisplayInfo();
        
        // 创建另一个对象
        Car yourCar = new Car("Honda", "Blue");
        yourCar.Accelerate(30);
        yourCar.DisplayInfo();
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 类和对象的关系就像饼干模具和饼干。类是同一种饼干的模具(如小熊饼干模具)，定义了饼干的形状和特征；对象则是用这个模具压出来的具体饼干，每个饼干是独立的，可以有不同的装饰(属性值)。你可以用一个模具(类)制作许多饼干(对象)，每个饼干都有相同的形状但可以有不同的颜色糖霜。</p>
        </div>

        <h2 id="section20">20. 构造函数与析构函数</h2>
        
        <h3>构造函数</h3>
        <p>构造函数在创建对象时初始化对象。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
    
    // 默认构造函数
    public Person()
    {
        Name = "Unknown";
        Age = 0;
        Console.WriteLine("默认构造函数被调用");
    }
    
    // 参数化构造函数
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
        Console.WriteLine("参数化构造函数被调用");
    }
    
    // 复制构造函数
    public Person(Person other)
    {
        Name = other.Name;
        Age = other.Age;
        Console.WriteLine("复制构造函数被调用");
    }
    
    public void Display()
    {
        Console.WriteLine($"姓名: {Name}, 年龄: {Age}");
    }
}

class ConstructorExample
{
    static void Main()
    {
        // 使用不同的构造函数
        Person person1 = new Person(); // 调用默认构造函数
        person1.Display();
        
        Person person2 = new Person("张三", 25); // 调用参数化构造函数
        person2.Display();
        
        Person person3 = new Person(person2); // 调用复制构造函数
        person3.Display();
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>
        
        <h3>析构函数</h3>
        <p>析构函数在对象被销毁前执行清理操作。</p>
        
        <div class="code-header">完整可运行示例</div>
        <div class="code-container">
            <pre><code>using System;

public class ResourceHandler
{
    private string resourceName;
    
    public ResourceHandler(string name)
    {
        resourceName = name;
        Console.WriteLine($"资源 {resourceName} 被创建");
    }
    
    public void UseResource()
    {
        Console.WriteLine($"使用资源 {resourceName}");
    }
    
    // 析构函数 (Finalizer)
    ~ResourceHandler()
    {
        // 清理非托管资源
        Console.WriteLine($"资源 {resourceName} 被清理");
    }
}

class DestructorExample
{
    static void CreateAndUseResource()
    {
        ResourceHandler resource = new ResourceHandler("临时文件");
        resource.UseResource();
        // resource 超出作用域，将成为垃圾回收候选对象
    }
    
    static void Main()
    {
        CreateAndUseResource();
        
        // 强制垃圾回收（仅用于演示，实际开发中通常不需要手动调用）
        GC.Collect();
        GC.WaitForPendingFinalizers();
        
        Console.WriteLine("主程序结束");
    }
}</code></pre>
            <button class="copy-btn" onclick="copyCode(this)">复制代码</button>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 构造函数就像新房交付前的装修工作，确保房子(对象)在交付使用时已经配置好基本设施(初始化字段)。析构函数则像退租前的清理工作，确保房间恢复原状，所有个人物品带走，水电煤气关闭(释放资源)。不同参数的构造函数就像提供不同档次装修套餐，满足不同需求。</p>
        </div>

        <h2 id="section21">21. 总结与后续学习方向</h2>
        <p>本笔记涵盖了C#的基础语法和编程概念，为进一步学习打下基础。</p>
        
        <h3>后续学习建议</h3>
        <ul>
            <li><strong>面向对象编程</strong>：深入学习继承、多态和抽象</li>
            <li><strong>异常处理</strong>：try-catch-finally语句</li>
            <li><strong>集合</strong>：List, Dictionary, Array等</li>
            <li><strong>LINQ</strong>：语言集成查询</li>
            <li><strong>异步编程</strong>：async/await关键字</li>
            <li><strong>泛型</strong>：提高代码的复用性和类型安全</li>
            <li><strong>委托和事件</strong>：C#中的函数指针和事件机制</li>
        </ul>
        
        <div class="note">
            <p><strong>学习资源：</strong> 官方文档(MSDN)、Pluralsight、C# in Depth等书籍，以及Microsoft Learn平台。</p>
        </div>
        
        <div class="key-concept">
            <p><strong>学习建议：</strong> 函数是实现封装这一思想的关键技术手段。先学会把代码打包成函数（工具），然后再学会用封装的思想把这些工具和数据合理地组织起来，藏起危险的，暴露有用的，最终构建出安全、稳定、易用的复杂程序。</p>
        </div>

        <div class="analogy">
            <p><strong>现实比喻：</strong> 学习编程就像学习做菜。本笔记教你认识了各种食材(数据类型)和厨房工具(语法结构)，以及切菜炒菜的基本技巧(函数和方法)。接下来你需要学习如何组合这些技能做出完整菜肴(面向对象)，如何处理做饭中的意外情况(异常处理)，如何高效准备宴席(异步编程)，以及如何创建自己的独特食谱(设计模式)。记住，好厨师不是只知道食材和工具，而是懂得如何巧妙组合它们做出美味佳肴。</p>
        </div>
    </div>

    <script>
        // 复制代码功能
        function copyCode(button) {
            const codeBlock = button.previousElementSibling;
            const textArea = document.createElement('textarea');
            textArea.value = codeBlock.textContent;
            document.body.appendChild(textArea);
            textArea.select();
            document.execCommand('copy');
            document.body.removeChild(textArea);
            
            // 显示复制成功反馈
            const originalText = button.textContent;
            button.textContent = '已复制!';
            setTimeout(() => {
                button.textContent = originalText;
            }, 1500);
        }
        
        // 为所有代码块添加复制按钮
        document.addEventListener('DOMContentLoaded', function() {
            const codeBlocks = document.querySelectorAll('pre');
            codeBlocks.forEach(block => {
                const button = document.createElement('button');
                button.className = 'copy-btn';
                button.textContent = '复制代码';
                button.onclick = function() { copyCode(this); };
                block.parentNode.insertBefore(button, block.nextSibling);
            });
        });
    </script>
</body>
</html>