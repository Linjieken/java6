# java6
## java实验五
### 1.实验目的
分析学生选课系统
使用GUI窗体及其组件设计窗体界面
完成学生选课过程业务逻辑编程
基于文件保存并读取数据
处理异常
### 2.实验要求
一、系统角色分析及类设计
例如：学校有“人员”，分为“教师”和“学生”，教师教授“课程”，学生选择课程。
定义每种角色人员的属性，及其操作方法。
属性示例：	人员（编号、姓名、性别……）
教师（编号、姓名、性别、所授课程、……）
			学生（编号、姓名、性别、所选课程、……）
			课程（编号、课程名称、上课地点、时间、授课教师、……）
二、要求:
1、设计GUI窗体，支持学生注册、课程新加、学生选课、学生退课、打印学生选课列表等操作。
2、基于事件模型对业务逻辑编程，实现在界面上支持上述操作。
3、针对操作过程中可能会出现的各种异常，做异常处理
4、基于输入/输出编程，支持学生、课程、教师等数据的读写操作。
5、基于Github.com提交实验，包括实验SRC源文件夹程序、README.MD实验报告文档。
### 3.核心代码
    public static void outText(String[] s) {
        File file = new File("C:\\Users\\Surface\\Desktop\\1234.txt");
        if(!file.exists()){//文件不存在
            file.mkdir();//创建文件
        }
        int number = 1;
        OutputStream os = null;
        try {
            os = new FileOutputStream("C:\\Users\\Surface\\Desktop\\1234.txt");

            PrintWriter pw = new PrintWriter(os);
            for (int i = 0; i < s.length; i++) {
                if (s != null) {
                    pw.println(s);//每输入一个数据，自动换行，便于我们每一行每一行地进行读取
                    //pw.print(s+",");//不会自动换行，必要时可以自己添加分隔符
                }
            }
            pw.close();//关闭资源
            os.close();//关闭资源
        } catch (FileNotFoundException e) {
            e.printStackTrace();
            System.out.println("异常信息：" + e.getMessage());
        } catch (IOException e) {
            e.printStackTrace();
            System.out.println("异常信息：" + e.getMessage());
        }
    }
读取文件

        public static String readText() {
        String filetext = null;//读取的信息
        int num = 0;
        char[] buf = new char[1024];
        //打开文件
        FileReader fr = null;
        try {
            fr = new FileReader("C:\\Users\\Surface\\Desktop\\1234.txt");
            BufferedReader br = new BufferedReader(fr); // 建立一个对象，它把文件内容转成计算机能读懂的语言
            //取出字符存到buf数组中
            while ((num = br.read(buf)) != -1) {
                //String(char[] cbuf,a,b),从cbuf的位置a开始取出连续的b个char组成字符串
                filetext = new String(buf, 0, num);
                System.out.println(filetext);
            }
            for (int i = 0; i < 10; i++) {
                System.out.print(buf[i] + " - ");
            }
        } catch (FileNotFoundException e) {
            e.printStackTrace();
            System.out.println("异常信息：" + e.getMessage());
        } catch (IOException e) {
            e.printStackTrace();
            System.out.println("异常信息：" + e.getMessage());
        }
写入文件
### 4.实验结果
![images](https://github.com/Linjieken/java6/blob/master/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20191209001207.png)
学生选课页面

![images](https://github.com/Linjieken/java6/blob/master/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20191209001332.png)
学生选课打印页面

![images](https://github.com/Linjieken/java6/blob/master/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20191209001233.png)
txt文件的读取与写入
### 5.实验感想
这次的实验涉及的范围较为广阔、全面，也是对于综合能力的考量。在设置GUI窗体支持学生注册这一项中，我遭遇了很大的挑战。即使我不断调试代码，但代码并没有运行成功。基于上次实验的学生选课、退课、打印，这次实验完成了任务中的文件的读取与写入以及异常处理。我深深地感觉到了自己的不足。在接下来的日子中，我一定认真研究java语言，尽早完成学生注册这一实验要求。
