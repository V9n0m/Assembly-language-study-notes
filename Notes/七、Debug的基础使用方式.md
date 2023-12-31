### How to Debug？
***
**汇编语言不区分大小写**

在DosBox中使用Debug功能，首先跟之前一样要进行挂载``` mount c: d:\MASM ``` ，挂载完之后切换到盘符C：然后输入debug就可以使用debug了。 
<div align = "center">
  <img src = "https://github.com/V9n0m/Assembly-language-study-notes/assets/81289456/b48e4a21-faf6-4171-9f6a-ba34b402aeac" width = 60% />
</div>

***

### -r命令
R命令的作用是查看和修改debug模式下CPU中寄存器的值，在下图中可以看到之前提到过的各种寄存器。
<div align = "center">
  <img src = "https://github.com/V9n0m/Assembly-language-study-notes/assets/81289456/d3a0a58a-9f69-41a6-aced-82326c3878d7" width = 60% />
</div>

### -d命令
D命令的作用是查看内存中的内容，在下图中可以看到073F:0100是一种表示内存的方式，用白话讲就是073F段空间中的0100单元，073F是段地址，0100是偏移地址。对应的后面的内容就是对应地址中的内容，都是用16进制表示的。

D命令默认会显示寻址地址开始的后128个内存单元的内容，以16进制的方式显示(每个内存单元8位，一行最多16个内存单元)，而最右边会将内存单元中的二进制数据以ascll码的形式翻译展示
<div align = "center">
  <img src = "https://github.com/V9n0m/Assembly-language-study-notes/assets/81289456/e4983548-7d80-49fc-b2b2-ce7231957aac)" width = 60% />
</div>

除此之外我们还可以通过``` d 1000:0 f ``` ， 或者 ``` d 1000:0 50 ``` 这种方式去查看在特定偏移区间内的内存数据
<div align = "center">
  <img src = "https://github.com/V9n0m/Assembly-language-study-notes/assets/81289456/34eb7567-dedf-49db-99a9-1737150bd9e3" width = 60% />
</div>

### -e命令
E命令的作用是改变内存中的内容，可以用``` e 1000:0 数据1 数据2 数据3 ``` 这种方式去修改指定内存中的数据，然后用 ``` d 1000:0 ``` 来查看是否修改成功。
<div align = "center">
  <img src = "https://github.com/V9n0m/Assembly-language-study-notes/assets/81289456/361ce434-e6df-41aa-b45c-fd6dff5d74cb" width = 60% />
</div>

除此之外还可以通过使用``` e 1000:0 ```这种方式修改，与上一中方式不同的是，这种方式输入指令后会先给你原来的数据，然后.后面的就是重新输入的新数据，空格之后就会出现下一个原来的数据。
<div align = "center">
  <img src = "https://github.com/V9n0m/Assembly-language-study-notes/assets/81289456/8f94c7b6-04e3-48a7-b164-eddbf574ee3f" width = 60% />
</div>

### -u命令
U命令的作用是将内存中的二进制数据转换为汇编指令展示(反汇编)
D命令能够将内存中的数据以16进制或ascll码的形式展现出来，但有时我们需要观察的是内存中的机器指令时，D命令的视图过于抽象，不利于理解。debug提供了U命令来解决这个问题。

通过 ``` u 073F:0100 ``` 可以将内存中的数据以汇编语言指令的形式进行展示。
<div align = "center">
  <img src = "https://github.com/V9n0m/Assembly-language-study-notes/assets/81289456/3df69325-5083-4c58-a235-d501efb56187" width = 60% />
</div>

### -a命令
A命令的作用是能够以汇编指令的形式，向内存中写入内容，前面我们知道e命令可以以十六进制的形式向内存中写入内容，但是这种形式相对于a命令来说太复杂了，有了a命令我们就可以直接向内存中写入汇编指令了。
<div align = "center">
  <img src = "https://github.com/V9n0m/Assembly-language-study-notes/assets/81289456/b54f7279-af6f-46b9-9124-bb3dc3509be3" width = 60% />
</div>

### -t命令
T命令的作用是单步机器指令的调试，直接就是-t，有点像其他语言程序Debug打完断点后，进行下一步的操作。
<div align = "center">
  <img src = "https://github.com/V9n0m/Assembly-language-study-notes/assets/81289456/5170164c-8e24-430e-8978-613ca6bceb1c" width = 60% />
</div>

### -q命令
退出


