## vim 常用命令

> 眼界决定高度，思路决定出路



##### 操作多个文件

- `vim *.conf`, 其中`conf`代表后缀
- 多文件切换 `:bn` 

#####  行号

- 命令模式  `:set nu`

##### 复制和粘贴

- 复制至行尾 `yG`
- 复制所在行`yy`
- 复制多行 `nyy`,其中`n`代表行数
- 粘贴 `p`

##### 跳转

- 行首 `shift +6`
- 行尾 ` n+$`  其中`n` 代表数字

##### 删除/剪切

- 删除单行 `dd`
- 删除多行 `:7,10d`

##### 撤销和恢复撤销

- 撤销 `u`
- 恢复撤销 `ctrl+r `

##### 搜索

- `/搜索字符串` , 回车
- 查看下一个匹配`n`