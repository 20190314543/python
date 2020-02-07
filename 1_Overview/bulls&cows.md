# 猜数字游戏

## 简单的猜数游戏

```mermaid
graph TB;
    st(开始)-->op(产生随机数)-->io(用户输入猜测)-->co{是否正确}
    co--no-->bs{判断大小}
    bs--big-->prbig(提示猜大了)-->io
    bs--small-->prsmall(提示猜小了)-->io
    co--yes-->pryes(猜对了)-->guessagain{继续猜}
    guessagain--yes-->op
    guessagain--no-->e(结束)

```

## 高级版本游戏规则
 
通常由两个人玩，一方出数字，一方猜。出数字的人要想好一个没有重复数字的4个数，不能让猜的人知道。猜的人就可以开始猜。每猜一个数字，出数者就要根据这个数字给出几A几B，其中A前面的数字表示位置正确的数的个数，而B前的数字表示数字正确而位置不对的数的个数。

如正确答案为 5234，而猜的人猜 5346，则是 1A2B，其中有一个5的位置对了，记为1A，而3和4这两个数字对了，而位置没对，因此记为 2B，合起来就是 1A2B。

接着猜的人再根据出题者的几A几B继续猜，直到猜中（即 4A0B）为止。

猜数字游戏通常设有猜测次数的上限。根据计算机测算，如果采用严谨的猜测策略，任何数字最多7次就可猜出（即达到 4A0B）。值得注意的是，在有些地方把次数上限定义为最多几次猜测以后就可以肯定数字是几，但这时或还需要再猜一次才能得到 4A0B 的结果。

标准的猜数字游戏由10个数码（0-9）和4个数位组成。可以通过变化数码或数位来丰富游戏。例如，可以使用9个数码玩4个数位的游戏。

```mermaid
graph TB;
    st(开始)-->op(产生4位随机数)-->io(用户输入4位数字猜测)-->co{判断结果是否正确}
    co--no-->bs(输出猜测结果)-->io
    co--yes-->pryes(猜对了)-->guessagain{继续猜}
    guessagain--yes-->op
    guessagain--no-->e(结束)

```

## 变体游戏规则

猜数字游戏的一种变体允许重复的数码。这种规则的游戏被称为 Mastermind。其规则大致为：

除了上面的规则外，如果有出现重复的数字，则重复的数字每个也只能算一次，且以最优的结果为准。例如，如正确答案为5543，猜的人猜5255，则在这里不能认为猜测的第一个5对正确答案第二个，根据最优结果为准的原理和每个数字只能有一次的规则，两个比较后应该为1A1B，第一个5位子正确，记为1A；猜测数字中的第三个5或第四个5和答案的第二个5匹配，只能记为1B。当然，如果有猜5267中的第一个5不能与答案中的第二个5匹配，因此只能记作1A0B。
