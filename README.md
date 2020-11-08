## 一、阅读程序（代码）
``` 
package jiekouchengxu;
public class Testjiekou {
	public static void main(String args[]) {
		Student doc1=new Student("张三","男",20);
		Teacher doc2=new Teacher("张三","男",20);
		Doctor doc3=new Doctor("张三","男",20);
		Student doc4=new Student("李四","女",20);
		Teacher doc5=new Teacher("李四","女",20);
		Doctor doc6=new Doctor("李四","女",20);
		doc2.setxinshui(20000);
		doc1.setxuefei(15000);
		System.out.println(doc1.name+doc1.sex+doc1.age+"学费"+doc1.tuition+"薪水"+doc2.salary+"交税"+doc3.jiaoshui(doc2,doc1));
		System.out.println(doc2.name+doc2.sex+doc2.age+"学费"+doc1.tuition+"薪水"+doc2.salary+"交税"+doc3.jiaoshui(doc2,doc1));
	}
}

package jiekouchengxu;
interface boshi extends laoshi,xuesheng{
	public double jiaoshui(Teacher a,Student b);
	
}
public class Doctor implements boshi{
	public String name;
	public String sex;
	public int age;
	public int salary;
	public int tuition;
	public double jiaoshui(Teacher a,Student b) {
		if ((a.salary-b.tuition)*0.03>0)
		{return (a.salary-b.tuition)*0.03;}
		else 
			return 0;
	}
	Doctor(String name,String sex,int age){
		this.name=name;
		this.sex=sex;
		this.age=age;
	}
	@Override
	public void setxinshui(int salary) {
		// TODO Auto-generated method stub
	}
	@Override
	public String yesxinshui() {
		// TODO Auto-generated method stub
		return null;
	}
	@Override
	public String noxinshui() {
		// TODO Auto-generated method stub
		return null;
	}
	@Override
	public void setxuefei(int xuefei) {
		// TODO Auto-generated method stub
	}
	@Override
	public void chaxuefei() {
		// TODO Auto-generated method stub
	}
}

package jiekouchengxu;
interface laoshi {
	void setxinshui(int salary);
	String yesxinshui();
	String noxinshui();
}
public class Teacher extends Doctor implements laoshi{
	Teacher(String name, String sex, int age) {
		super(name, sex, age);
			this.name=name;
			this.sex=sex;
			this.age=age;
		// TODO Auto-generated constructor stub
	}
	//定义老师的属性
	String s = "";
	public String name;
	public String sex;
	public int age;
	public int salary;
	@Override
	public void setxinshui(int salary) {
		// TODO Auto-generated method stub
		this.salary=salary;
	}
	@Override
	public String yesxinshui() {
		// TODO Auto-generated method stub
		return s = "yifaxinshui";		
	}
	public String noxinshui() {
		// TODO Auto-generated method stub
		return s = "meifaxinshui";		
	}
}

package jiekouchengxu;
interface xuesheng {
	void setxuefei(int xuefei);
	//void yesxuefei();
	void chaxuefei();
}
public class Student extends Doctor implements xuesheng{
	Student(String name, String sex, int age) {
		super(name, sex, age);
		this.name=name;
		this.sex=sex;
		this.age=age;
		// TODO Auto-generated constructor stub
	}
	//定义学生的属性
	public String name;
	public String sex;
	public int age;
	public int tuition;
	@Override
	public void setxuefei(int xuefei) {
		// TODO Auto-generated method stub
		this.tuition=xuefei;
	}
	@Override
	public void chaxuefei() {
		// TODO Auto-generated method stub
}
``` 

## 二、实验要求
<br>1、在博士研究生类中实现各个接口定义的抽象方法;
<br>2、对年学费和年收入进行统计，用收入减去学费，求得纳税额；
<br>3、国家最新纳税标准（系数），属于某一时期的特定固定值，与实例化对象没有关系，考虑如何用static  final修饰定义；
<br>4、实例化研究生类时，可采用运行时通过main方法的参数args一次性赋值，也可采用Scanner类实现运行时交互式输入；
<br>5、根据输入情况，要在程序中做异常处理。

## 三、实验目的
<br>1、掌握Java中抽象类和抽象方法的定义； 
<br>2、掌握Java中接口的定义，熟练掌握接口的定义形式以及接口的实现方法；
<br>3、了解异常的使用方法，并在程序中根据输入情况做异常处理。

## 四、实验过程
<br>1、先想好大概思路,建立四个class(Test,Doctor,Teacher,Student)。在Doctor里面定义博士的属性，把它当成父类，这样就可以在Teacher和Student里面继承父类，本来想的是让Doctor继承老师和学生的，但一个子类只可以继承一个父类，但父类可以被多个子类继承。
<br>2、在Teacher类里面需要定义老师的属性，并建立一个接口，用来查看是否发薪水。
<br>3、在Student类里面需要定义学生的属性，并建立一个接口，用来查看是否交学费。

## 五、核心方法
<br>Teacher类：
<br>interface laoshi {
	<br>void setxinshui(int salary);
	<br>String yesxinshui();
	<br>String noxinshui();
<br>}
<br>Student类：
<br>interface xuesheng {
	<br>void setxuefei(int xuefei);
  <br>void yesxuefei();
	<br>void chaxuefei();
<br>}


## 六、实验结果
张三男20学费15000薪水20000交税150.0

## 七、实验感想
了解了接口的定义方法，还知道了报错机制。
