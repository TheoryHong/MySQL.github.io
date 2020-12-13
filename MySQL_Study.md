## 第四章：SQL处理数据的高级方法 

## 1.MySQL的正则表达式搜索(Regular Expression-RE)  
1. 之前是通过匹配、比较、通配符来寻找数据，但是随着过滤条件的复杂性，我们需要使用正则表达式，来**匹配文本**的特殊的串（字符集合）
_将一个模式（正则表达式）与一个文本串进行比较_   
2. 场景：1）文本中提取电话号码；2）名字中有数字的文件；3) 文本中所有重复的单词；4）替代URL为html
3. **MySQL用where子句对正则表达式提供了初步支持，允许你指定正则表达式，过滤select检索出的数据。**  

**正则表达式的语句：Table中数列的名字 REGEXP + 单引号 + 正则表达式的符号：数字、|、[  ] + 分号 

### 1.基本字符串匹配 
1）找到含产品名称中含1000的字样
a. 传统方法：
```
select * from products where
prod_name like '%1000'; 

```
b.使用正则表达式：
```
select * from products where
prod_name REGEXP '1000' 

```
 
 ### 2. 匹配000相关的产品信息 
```
select * from products where
prod_name like '%000';

select * from products WHERE
prod_name REGEXP '.000'; 

```

### 3.使用or的方法进行匹配   #| 
找到含产品名称中含1000或2000的字样
```
select * from products WHERE
prod_name REGEXP '1000|2000'; 

```  

### 4.使用范围方法进行匹配  #中括号
```  
select * from products WHERE
prod_name REGEXP '[12]000';
```  
_中括号代表范围[1-4],表示括号里面是[1、2、3、4]：中括号里面代表一个字符、出现的可能性


### 5.使用范围和使用or同步进行 
```  
select * from products WHERE
prod_name REGEXP '[1|2]000';  
```  











You can use the [editor on GitHub](https://github.com/sophieloveforlearning/sophielearner.github.io/edit/main/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/sophieloveforlearning/sophielearner.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
