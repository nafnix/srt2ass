# srt2ass

该脚本基于python3.8.5进行开发，使用较老的版本可能会引发一些未知的故障，建议使用Python3.6以上版本运行。

## 支持编码

该脚本支持如下编码`utf-8`、`utf-16`、`utf-32`、`gbk`、`gb2312`、`gb18030`、`cp1252`、`big5`

## 使用示例

### 直接

你可以直接打开文件，然后srt2ass.py会扫描当前目录下所有以`.srt`为后缀的文件，然后询问你是否要转换它们。如果你输入了`yes`，那么就会将进行转换。

**注意**：转换会把原有的ass文件覆盖。也就是说如果你当前目录下有`a.srt`和`a.ass`，如果你再尝试启动`srt2ass.py`脚本，那么你原来的`a.ass`将会被覆盖。

### 命令行

```
python srt2ass.py filename1.srt
```

如果你有多个文件，也可以执行

```
python srt2ass.py filename1.srt filename2.srt
```

filename对应着你的文件名，含`.srt`后缀

### 作为模块使用

#### 导入模块

```python
import srt2ass
```

#### 指定文件名获取内容

```python
srtFile_To_assFile = srt2ass.srt_to_ass(filename=filename)
```

如果不出意外，那么此时你将获得转换为`ass`格式后的字符串

#### 通过srt格式的字符串获取转换为ass后的字符串

有时候我们可能已经在外部已经打开了文件并且获取了文件内容，我们不想再在srt2ass中再打开一次，所以也可以直接传入内容。

通过`content`参数我们可以获取转换为`ass`后的字符串

```python
srtContent_To_assContent = srt2ass.srt_to_ass(content=content)
```

### 更多的参数

#### json格式返回值

如果想获取json格式可以加上`for_json`参数：

```python
sta = srt2ass.srt_to_ass(filename=filename, for_json=True)
```

返回的json格式为
```json
{
  "time": "转换所耗费的时间，浮点数格式",
  "content": "转换后的内容"
}
```

#### 指定编码打开文件

可能你的文件编码格式在该脚本所支持的编码格式之外，可以添加`encoding`参数告诉脚本你的文件编码：

```python
sta = srt2ass.srt_to_ass(filename=filename, encoding='文件编码')
```

#### 指定头部

可能你注意到有个header.txt文件。里面存放着你转换为ass文件之后的头部，我不太了解ass的格式(事实上srt我也不了解，甚至我对所有字幕格式都一无所知)，你可以自行修改它，以便使用。

除此之外，你也可以指定自己的头文件：

```python
sta = srt2ass.srt_to_ass(filename=filename, header_path='头文件路径')
```

如果你喜欢这个脚本，请点个star
