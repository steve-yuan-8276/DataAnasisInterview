# How to implement full outer join in Alteryx

The Alteryx Join tool contains three output anchors - J (Join), L (Left), and R (Right) - which correspond to the three basic data merging methods:

- J (Join) Output Anchor - This is the output of "Inner Join", which only contains records that match both data sources.
- L (Left) Output Anchor - This is the output of "Left Outer Join" and includes all records from the left input. If there are matching records on the right input, corresponding data will also be merged; otherwise, these fields will be empty.
- R (Right) Output Anchor - This is the output of "Right Outer Join" and includes all records from the right input. If there are matching records on the left input, corresponding data will also be merged; otherwise, these fields will be empty.

If you need to complete a "Full Outer Join," Alteryx does not have a direct operation to do so but can be achieved through following steps:

- Use one Join tool to complete Inner Join.
- Use two additional Join tools respectively for Left and Right outer join, and output unmatched records on both sides separately.
- Merge results from Inner Join, Left Only, and Right Only using Union tool to achieve Full Outer Join effect.

Through this method, you can combine various tools in Alteryx to simulate all types of Joins in SQL including Full Outer Joins. When designing workflows, you can use one or more join tools to merge multiple Excel files then adjust their join types based on your business needs.



Alteryx Join工具包含三个输出锚点 —— J（Join），L（Left），和 R（Right）—— 分别对应于三种基本的数据合并方式：
- J (Join) Output Anchor – 这是“Inner Join”的输出，只包含在两个数据源中同时匹配的记录。
- L (Left) Output Anchor – 这是“Left Outer Join”的输出，包含所有左边输入端的记录。如果在右边输入端有匹配的记录，相应数据也会被合并进来；如果没有匹配，则这些字段会为空。
- R (Right) Output Anchor – 这是“Right Outer Join”的输出，包含所有右边输入端的记录。如果在左边输入端有匹配的记录，相应数据也会被合并进来；如果没有匹配，则这些字段会为空。

如果您需要完成一个“Full Outer Join”，Alteryx没有直接的一个操作可以完成，但可以通过以下步骤实现：
- 使用一个Join工具来完成Inner Join。
- 用两个附加的Join工具分别完成Left和Right outer join，将左右两边不匹配的记录分别输出。
- 将Inner Join的结果、Left Only的结果、以及Right Only的结果使用Union工具合并起来，就可以得到Full Outer Join的效果。

通过这种方法，你可以组合Alteryx中的各种工具来模拟SQL中所有类型的Join，包括Full Outer Join。设计工作流时，你可以通过一个或多个Join工具来合并多个Excel文件，然后根据你的业务需求调整它们之间的Join类型。
