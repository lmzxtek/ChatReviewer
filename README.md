
<div style="font-size: 1.5rem;">
  <a href="./README.md">中文</a> |
  <a href="./readme_en.md">English</a>
</div>
</br>
<h1 align="center">ChatReviewer</h1>
<div align="center">
  <a href="https://github.com/nishiwen1214/ChatReviewer">
    <img src="https://github.com/nishiwen1214/ChatReviewer/blob/main/images/chatreviewer.png" width="600">
  </a>
 </div>
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

⭐️**很多人留言没ChatGPT的API-key....不会申请的可以加我微信"Shiwen_Ni"(注：本人不卖号，真不会的可找我，备注api)**

**ChatReviewer收到了大多数人的肯定，同时也收到少数质疑和担忧。**

**因此，为了防止极少数人直接使用生成的内容进行论文审稿，在每次生成的内容最后加上了的伦理声明，**

**输出中间插入了警告：Generated by ChatGPT, no copying allowed! （为了伦理安全，只能牺牲内容的可读性~）**

**从生成的内容里扣字，不如直接使用ChatGPT更有效率，相信可以防止有人使用该工具对分配的论文进行审稿。**

**该工具帮助了不少人从审稿人角度对论文进行快速的总结和评估，提高了科研和学习的效率，目前看来是利大于弊。**

**如果谁有更好的方法来限制少数人的不规范使用，欢迎留言，为科研界做一份贡献。**

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

💥💥💥**ChatReviewer的第一版网页出来了！！！ 直接点击：https://huggingface.co/spaces/ShiwenNi/ChatReviewer**
![image](https://user-images.githubusercontent.com/56249874/236391740-e3c0c142-db5f-436b-b8ab-86502c7b0428.png)
💥💥💥**ChatResponse的第一版网页也出来了！！！ 直接点击：https://huggingface.co/spaces/ShiwenNi/ChatResponse**
![image](https://user-images.githubusercontent.com/56249874/227842231-21c5e7b5-fbe6-46d7-b7d3-45b24fec0765.png)

<strong>ChatReviewer是一款基于ChatGPT-3.5的API开发的智能论文分析与建议助手。</strong>其用途如下：
⭐️对论文的优缺点进行快速总结和分析，提高科研人员的文献阅读和理解的效率，紧跟研究前沿。
⭐️对自己的论文进行分析，根据ChatReviewer生成的改进建议进行查漏补缺，进一步提高自己的论文质量。

**ChatResponse是一款根据审稿人的评论自动生成作者回复的AI助手。用途如下：**
⭐️根据收到的审稿意见，ChatResponse自动提取其中各个审稿人的问题和担忧，并生成点对点的回复。

基于之前ChatPaper的启发，本人在周末开发了这款ChatReviewer，并且开源给大家。欢迎大家使用、提问和转发！

♥本项目是本人利用休息时间进行更新，如果对您有帮助，欢迎Star和Fork，也欢迎您进行赞助！♥

**⭐️⭐️⭐️ 声明：请对审稿的论文负责，不要直接复制粘贴ChatReviewer生成的任何审稿意见！！！**

## 主要更新：
- 💥**增加了ChatResponse的网页版！** 2023/3/27
- 💥💥💥**为了方便没有太多计算机背景的人的使用，经过本人昨晚上的辛苦加班TAT，ChatReviewer的第一版网页出来了！！！**  2023/3/22
- 重写了section split的逻辑, fix了可能抓不到固定标题的问题；修改prompt机制：先询问chatgpt 它感兴趣的章节, 随后再发送相应的章节。2023/3/21
- **更新了ChatResponse，这个是根据审稿人的评论自动生成作者回复的AI助手。**（ChatResponse和ChatReviewer有点左右互博的意思...） 2023/3/19
- 增加了Docker部署的方式。将服务部署在自己的服务器上，速度更快，更安全。一行命令可以部署两个服务。2023/5/28


## 使用步骤：
Windows, Mac和Linux系统都可，python版本最好是3.8或3.9，因为低于3.8就不支持tiktoken这个包。
1. 在apikey.ini中填入你的openai的api key（sk开头的那串，如果真不会可以加我微信"Shiwen_Ni"(注：本人不卖号，真不会的可以找我))
2. 使用过程要使用VPN而且保证全局代理（因为ChatGPT把中国ban了）。
3. 在ReviewFormat.txt中输入你想要的特殊审稿格式（不然就是默认格式）。
![image](https://user-images.githubusercontent.com/56249874/226108813-dc44924f-5528-4644-aed2-475d23ccdd84.png)
4. 安装依赖：使用VPN。
``` bash
pip install -r requirements.txt
```
或者使用国内镜像：
```bash
pip install -r requirements.txt -i  http://pypi.douban.com/simple  --trusted-host pypi.douban.com
```
5. 对本地的论文进行分析： 运行chat_reviewer.py， 比如：
```python
python chat_reviewer.py --paper_path "input_file/demo1.pdf"
```
对本地的论文进行批量分析： 运行chat_reviewer.py， 比如：
```python
python chat_reviewer.py --paper_path "input_file"
```
Docker部署：

```
docker run -d -p 7000:7000 -p 8000:8000 hanhongyong/chatreviewer:latest
```

其中，7000端口为ChatReviewer服务，8000端口为ChatResponse服务。注意：本服务一定要部署在国外服务器上！

## 例子：
![image](https://user-images.githubusercontent.com/56249874/226351967-ef0e6f61-457a-4a77-b78f-84bde47ac38c.png)

## 使用ChatResponse
对本地的审稿评论review_comments.txt进行回复： 运行chat_response.py， 比如：
```python
python chat_response.py --comment_path "review_comments.txt"
```
例子：
![image](https://user-images.githubusercontent.com/56249874/226114965-9a2b91e5-3766-42e8-b17f-05d9abb2191b.png)

## 致谢：
- 感谢OpenAI提供的强大ChatGPT-API；
- 感谢[kaixindelele](https://github.com/kaixindelele)同学的[ChatPaper](https://github.com/kaixindelele/ChatPaper)和开源精神 ，ChatReviewer的代码是基于ChatPaper修改而来。



