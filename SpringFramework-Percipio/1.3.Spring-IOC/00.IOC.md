### **💡 Inversion of Control (IoC) in Spring Boot (Hinglish me)**

**IoC (Inversion of Control)** ek **design principle** hai jo object creation aur dependency management ko control karta hai. Normally, hum  **objects ko manually create karte hain** , par IoC me **Spring Container** automatically objects (beans) create aur manage karta hai.

---

## **✅ 1. IoC Kya Hai?**

IoC ka **main idea** yeh hai ki **control ko reverse** kar diya jaye. Matlab:

* Normally, hum **objects manually create** karte hain (`new` keyword se).
* IoC me  **Spring khud objects manage karta hai** .

💡 **Example:**

* Without IoC:
  ```java
  class Car {
      Engine engine = new Engine();  // Manual object creation
  }
  ```
* With IoC:
  ```java
  @Component
  class Car {
      @Autowired
      Engine engine;  // Spring automatically injects Engine
  }
  ```

### **📌 IoC Ka Benefit:**

✅ **Code loosely coupled hota hai.**

✅ **Object creation aur lifecycle Spring manage karta hai.**

✅ **Testing easy hoti hai.**

---

## **✅ 2. IoC Container Types in Spring**

Spring me IoC  **Container do tarah ke hote hain** :

### **1️⃣ BeanFactory** (Lightweight, used in microservices)

* **Ye ek basic IoC container hai** jo sirf objects ko create aur manage karta hai.
* **Lazy loading** karta hai (matlab objects tabhi bante hain jab zarurat ho).
* **Example:**
  ```java
  BeanFactory factory = new ClassPathXmlApplicationContext("beans.xml");
  Car car = (Car) factory.getBean("carBean");
  ```

### **2️⃣ ApplicationContext** (Advanced, mostly used in Spring Boot)

* **Advanced version hai jo extra features provide karta hai.**
* **Eager loading** karta hai (matlab objects pehle se create ho jate hain).
* **Spring Boot applications me ye hi use hota hai.**
* **Example:**
  ```java
  ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
  Car car = context.getBean(Car.class);
  ```

---

## **✅ 3. IoC Example in Spring Boot**

💡 **Hum IoC ka use Spring Boot me `@Component`, `@Autowired`, aur `@Configuration` se karte hain.**

### **📌 Step 1: Create a Bean (`@Component`)**

```java
import org.springframework.stereotype.Component;

@Component
class Engine {
    public Engine() {
        System.out.println("Engine Created!");
    }
    void start() {
        System.out.println("Engine Started!");
    }
}
```

### **📌 Step 2: Inject Dependency (`@Autowired`)**

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;

@Component
class Car {
    @Autowired
    Engine engine;

    void drive() {
        engine.start();
        System.out.println("Car is running...");
    }
}
```

### **📌 Step 3: Run the Application (`@SpringBootApplication`)**

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.ApplicationContext;

@SpringBootApplication
public class IoCExample {
    public static void main(String[] args) {
        ApplicationContext context = SpringApplication.run(IoCExample.class, args);
        Car car = context.getBean(Car.class);
        car.drive();
    }
}
```

### **📌 Output:**

```
Engine Created!
Engine Started!
Car is running...
```

---

## **✅ 4. Conclusion**

☑ **IoC ka matlab hai "Spring khud object creation aur dependencies manage kare".**

☑ **Spring Boot me IoC ko `@Component`, `@Autowired`, aur `ApplicationContext` se implement kiya jata hai.**

☑ **IoC ka fayda hai ki code loosely coupled hota hai, maintainable hota hai, aur testing easy ho jati hai.**

👉 **IoC ka next step hai Dependency Injection (DI), jisme Spring dependencies ko inject karta hai. Kya tum DI ka bhi deep explanation chahte ho? 😃**
