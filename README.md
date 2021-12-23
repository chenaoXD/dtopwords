## D-TopWords

### 代码运行

- 代码运行（需要在 linux 环境下运行）
  - 将 corpus.tar.gz (https://drive.google.com/file/d/0B_tvb3s-yy6fc1hzUGdSSzFNLTg/view?usp=sharing&resourcekey=0-y98wSlwjgFLjFzgShGrHxw) 的内容，解压到代码目录的 corpus/ 目录中
  - python pipeline src_path trg_path 即可自动运行全部代码，输出抽取出的领域新词
     - 例如：`python pipeline.py corpus/c4x@TsinghuaX@30240184X.txt results/result.txt`
  - 其中 src_path 是语料路径（例如学堂在线字幕路径无需分词，例如 corpus/c4x@TsinghuaX@30240184X.txt
  - 其中 trg_path 是输出路径
  - 结果样例参见 results/ 目录
- 可调节参数：
  - 参见 settings.py，其中包括每一个参数的具体说明


### 代码说明

算法以 D-Topwords 算法为基础，同时加上了两个后处理方法（lily 算法与 wikipedia pattern 记为一个）

#### D-Topwords 算法
- 利用 D-Topwords 作为基础，抽取出基本的候选词表
- 相关代码：
  - dtopwords.py: 主算法部分

#### 过滤算法 1： Wikipedia pattern based fitler
- 利用 wikipedia 抽取出的模板来对词表进行过滤（其中包含了 lily 算法中的正模板）。
- 过滤算法参见 pipeline.py 中 filter_by_threshold() 函数
- 相关代码：
  - pipeline.py: 利用模板过滤的功能代码
  - wiki_processor.py: 模板抽取代码（如果不考虑自己重新抽取模板则不需要执行）

#### 过滤算法 2：ABC pattern based fitler
- 利用标记出的短语模板，进行能够保证正确性的过滤
- 过滤算法参见 rule0.py
- 相关代码：
  - rule0.py: 利用标记出的短语模板，进行能够保证正确性的过滤(通过实验随后选取了效果较好的后处理)
  

### 算法应用于《数据结构》课程 (前 50)
```
遍 历	0.003696	18
关 键 码	0.003087	43
复 杂 度	0.002689	45
递 归	0.002382	48
运 算 符	0.002004	26
B S T	0.001995	43
左 孩 子	0.001981	62
B 树	0.001915	103
数 据 结 构	0.001889	62
右 子 树	0.001807	46
前 缀	0.001757	46
根 节 点	0.001572	51
右 孩 子	0.001549	12
红 黑 树	0.001229	47
左 括 号	0.001200	16
所 对 应	0.001198	18
子 序 列	0.001190	13
左 子 树	0.001137	19
忽 略 掉	0.001117	14
A V L 树	0.001083	28
入 栈	0.001076	8
z i g	0.001067	8
二 叉 树	0.001057	23
父 节 点	0.001024	25
模 式 串	0.001021	54
词 条	0.000988	23
括 号	0.000960	20
栈 顶	0.000957	20
首 元 素	0.000952	19
递 归 实 例	0.000934	10
优 先 级	0.000926	12
字 符	0.000918	40
向 量	0.000916	132
右 括 号	0.000912	16
栈 中	0.000871	6
l o g n	0.000841	21
有 序 向 量	0.000828	18
逆 序	0.000794	46
排 序	0.000778	13
后 缀	0.000760	7
操 作 数	0.000757	2
最 坏 的 情 况	0.000756	54
减 而 治 之	0.000735	11
删 除 操 作	0.000732	9
最 坏 情 况	0.000732	58
再 接 下 来	0.000731	15
前 驱	0.000721	20
计 算 成 本	0.000718	15
节 点	0.000709	313
```

### 相关论文

- Chen, Ao, and Maosong Sun. "Domain-Specific New Words Detection in Chinese." Proceedings of the 6th Joint Conference on Lexical and Computational Semantics (* SEM 2017). 2017.
