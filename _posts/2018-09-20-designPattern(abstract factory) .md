<!--
---
layout: post
date: 2018-09-20 14:31:10 +0800
title: Java
categories: Java
---
-->


## 设计模式:抽象工厂模式 ##

### 抽象工厂模式 ###
[转自](https://blog.csdn.net/wenzhi20102321/article/details/78153437)

** 模式定义 **

		为创建一组相关或相互依赖的对象提供一个接口，而且无需指定它们的具体类。
	
** 模式结构 **
	简单工厂模式包含如下角色:
1. AbstrFactory: 抽象工厂
	作用：创建不同组合的对象
2. ConcreteFactory:具体工厂
	
3. ConcreteProduct:具体产品角色
	是抽象工厂的具体实现
4. AbstractObject:抽象产品
	抽象产品接口
5. ConcreteObject:具体产品
	抽象产品的具体实现
** 模式实例与解析 **

	AbstractProduct:抽象产品
	
		public interface Benz{
			void carColor();
			void carSpeed();
			void carPrice();
		}
		
		public interface Navigator{
			void navigatorColor();
			void navigatorPrice();
		}
		
	ConcreteProduct:具体产品
		
		public class BenzC180 implements Benz{
			
			public BenzC180(){
				carColor();
				carSpeed();
				carPrice();
			}
			
			@Override
			public void carColor(){
				System.out.println("BenzC180's color is white");
			}
			
			@Override
			public void carSpeed(){
				System.out.println("BenzC180's speed is 320");
			}
			
			@Override
			public void carPrice(){
				System.out.println("BenzC180's price is 500000");
			}
		}
		
		public class BenzE260 implements Benz{
			
			public BenzE260(){
				carColor();
				carSpeed();
				carPrice();
			}
			
			@Override
			public void carColor(){
				System.out.println("BenzE260's color is black");
			}
			
			@Override
			public void carSpeed(){
				System.out.println("BenzE260's speed is 300");
			}
			
			@Override
			public void carPrice(){
				System.out.println("BenzE260's price is 450000");
			}
		}
		
		
		public class C180Navigator implements Navigator{
			
			public C180Navigator(){
				navigatorColor();
				navigatorPrice();
			}
			
			@Override
			public void navigatorColor(){
				System.out.println("C180Navigator's color is white");
			}
			
			@Override
			public void navigatorPrice(){
				System.out.println("C180Navigator's price is 5000");
			}
		}
		
		public class E260Navigator implements Navigator{
			
			public E260Navigator(){
				navigatorColor();
				navigatorPrice();
			}
			
			@Override
			public void navigatorColor(){
				System.out.println("E260Navigator's color is black");
			}
			
			@Override
			public void navigatorPrice(){
				System.out.println("E260Navigator's price is 4500");
			}
		}
		
		
	
	AbstractFactory: 抽象工厂
		public interface BenzFactory{
				Benz createCar();
				
				CarNavigator createNavigator();

		}
		
		
	ConcreteFactory:具体工厂
		
		public class C180Factory implements BenzFactory{
			@Override
			public Benz createCar(){
				return new BenzC180();
			}
			
			@Override
			public Navigator createNavigator(){
				return new C180Navigator();
			}
		}
		
		public class E260Factory implements BenzFactory{
			@Override
			public Benz createCar(){
				return new BenzE260();
			}
			
			@Override
			public Navigator createNavigator(){
				return new E260Navigator();
			}
		}
		
		
		
		
	示例:
		public class AbstractFactoryDemo{
			public static void main(String[] args){
				System.out.println("product BenzC180...");
				BenzFactory benzFactory = new C180Factory();
				benzFactory.createCar();
				benzFactory.createNavigator();
				
				System.out.println("========================");
				
				System.out.println("product BenzE260...");
				
				BenzFactory benzFactory2 = new E260Factory();
				benzFactory2.createCar();
				benzFactory.createNavigator();
			}
		}
		
**模式优缺点**

	优点:
		针对同一组产品创建新的生产线，只需实现那组产品的抽象工厂接口即可创建新的工厂类。
		如果需要生产新的汽车产品和对应的导航仪设备，你只需要创建一个该产品对应的具体工厂和该产品的具体实现类，不需要改变抽象的工厂类和抽象
的产品类，具体工厂类和具体产品类需要什么操作已经在抽象接口类定义好了。

	缺点:
	抽象工厂模式的扩展性就没那么好了。比如说某个工厂需要多创建几个产品对象，那么就需要增加抽象工厂的方法，增加抽象接口的方法后，其他实现了
抽象工厂接口方法的所有类都需要改变，才能正常编译。
抽象方法模式的最大缺点就是产品族本身的扩展非常困难。如果在产品族中增加一个新的产品类型，则需要修改多个接口，并影响现已有的工厂类。 
	
**模式适用环境**

	当一个对象都有相同的约束时，可以使用抽象工厂模式。 打个比方说，这个工厂的几个产品都需要经过某些共同的步骤和打上相同的商标，这一组产品
可以在一个工厂里面生产，减少很多重复的代码在不同的地方都出现多次。

	
	
	


