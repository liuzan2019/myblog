# 问题：

如下代码是否会生成多个对象

![](..\image\image-20220421165428345.png)

# 代码验证：

## 对象类1：

```java
@Data
public class DemoClass {
   public DemoClass(String name){
      this.name = name;
   }
   private String name;
}
```

## 对象类2：

```java
@Data
public class DemoWapper {
   public DemoWapper(DemoClass demoClass) {
      this.demoClass = demoClass;
   }
   private DemoClass demoClass;
}
```

## 配置类：

```java
@Configuration
public class TestConfig {
   @Bean(name = "demo1")
   public DemoClass getDemo1(){
      return new DemoClass(new Date().toString());
   }

   @Bean
   public DemoWapper getDemoWapper(){
      return new DemoWapper(getDemo1());
   }
}
```

## 验证类：

```java
@org.springframework.stereotype.Component
public class ComponentTest implements InitializingBean {
   @Autowired
   private DemoWapper demoWapper;

   @Autowired
   private DemoClass demoClass;

   @Override
   public void afterPropertiesSet() throws Exception {
      System.out.println(demoWapper.getDemoClass()==demoClass);
   }
}
```

## 结果：

![image-20220421174454762](..\image\image-20220421174454762.png)

## 结论：

配置类方法只执行一遍，只生成一个对象