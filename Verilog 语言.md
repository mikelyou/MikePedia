# Verilog 语言

Created: 2021-08-02

#电子电路/数字电路 #Language/Verilog

本文只介绍 Verilog 的语法，在数字电路中的使用会在 [[MikePedia/Verilog 应用]] 中讲述。

## 数据类型
最常用的两种：`wire`线网、`reg`寄存器，其余的可以理解为扩展或辅助。

### Wire 线网
线网（`wire` ）表示硬件元件之间的物理连线，若未连接，缺省值一般为 `Z`. 举例：

```verilog
wire interrupt;
wire flag1, flag2;
wire gnd = 1'b0;
```

### Reg 寄存器
寄存器（`reg`）用来存储单元，会保持数制不变，直到被改写。

整数（`integer`）、实数（`real`）、时间（`time`）都属于 reg 类型。

举例：

```verilog
reg dk_temp;
reg flag1, flag2;
```

### Vector 向量
[[位宽]]大于1的 wire 或 reg 可以声明为向量（Vector）形式。举例：

```verilog
reg [3:0] counter;
wire [31:0] gpio_data;
output reg [0:0] y; // 1 位宽，同时作为输出
output [0:0] y; //如不声明，默认为 wire 类型
input wire [3:-2] z; //负数也是可以的
input wire [-2:3] z; //递增也是可以的，但是一旦声明，必须按照递增使用
					// 因为容易出错，不建议混用。
reg counter [3:0]; //名称放在位宽之前，这种叫 unpacked array，目前用不到
					//常用的叫 packed array
assign out = my_vector[10]; //取第10位
/*待补充*/
```

### 数组
### 存储器
### 字符串

## 表达式
### 操作数
### 操作符
操作符有九种：算术、单目、关系、等价、逻辑、按位、归约、移位、拼接、条件。
## 编译指令
## 赋值 Assignment
赋值分为两种（目前）：连续赋值和过程赋值。
### 连续赋值 Continous Assignment
只能在[[过程]](always/initial)之外使用，用于对 wire 类型的赋值。

格式为：
```verilog
assign LHS_target = RHS_expression;
```

其中，左侧 `LHS` 必须是 wire类型或标量，不能是reg；而右侧 `RHS` 则没有类型的要求。

只要有数制变化导致 `RHS` 的值变化，就会立即进行计算并赋值给 `LHS`.

wire 型变量只能被赋值**一次**。

可以在声明的同时进行赋值。比如如下两种是等效的：
```verilog
wire A, B;
assign out = A & B;
```
```verilog
wire out = A & B;
/*  please check */
```


### 过程赋值
过程赋值是在[[过程]]（always/initial）中使用的赋值，用于对 reg 类型的赋值。这些变量在被赋值后保持不变，直到再次被赋值。

与连续赋值的区别：；，连续赋值总是激活的，任何数值改变都会影响结果；而过程赋值只有在语句执行时才有效。

过程赋值有两种：阻塞赋值和非阻塞赋值。

#### 阻塞赋值 Bloacked Assignment
顺序执行，在下一条语句执行前，当前语句一定会执行完毕。使用符号 `=`， 一般在 conbinational always 中使用。（`always @(*)`）

#### 非阻塞赋值 Non-Blocked Assignment
并行执行，与下一条语句是同时执行的。使用符号 `<=`（注意，这不是小于等于，而是箭头），一般在 clocked always 中使用。（`always @(posedge clk)`）


### 过程连续赋值
## 过程结构
## 时序控制
### 时延控制
### 事件控制

## 语句块
### 顺序
`begin end`
### 并行
`fork join`

## 条件语句
### IF 语句
`if-else if-else`
### CASE 语句
`case(condition) endcase`

特殊的，`casex` 和 `casez`.

## 循环语句
有四种：while, for, repeat, forever

## 模块
## 函数
## 过程
## 任务
## 状态机
## 竞争与冒险
## 避免 latch
## 仿真激励