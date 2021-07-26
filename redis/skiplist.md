# skiplist

这些列表的基本思想是删除时标记被删除结点的next指针以避免并发插入的冲突，并且在遍历时跟踪（前驱结点、结点、后继结点）三元组以检测何时以及如何解除已删除结点的链接

- 删除

定位结点，空值，附加删除标记，取消前驱结点链接，删除关联的索引结点，可能降低头部索引层次
只需要调用findPredecessor即可清楚索引结点。它将解除索引到被删除结点的链接，也包括到这个结点的索引。
这是无条件的，我们不能预先检测是否存在索引结点，因为在初始化搜索改结点时可能出现某些或所有索引尚未插入的情况，
并且我们希望没有垃圾保留，因此必须调用来确定

- findPredecessor

返回一个严格小于给定key的基层结点，如果没有这样的结点就返回基层header
解除索引到被删除结点的链接。