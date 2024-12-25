**Deep Copy** aur **Shallow Copy** do tarike hain kisi object ko duplicate karne ke liye. Dono ka kaam object ke ek duplicate banane ka hota hai, lekin inka behavior memory aur references ke perspective se alag hota hai.

### **1.Shallow Copy**

```plaintext
Original Person:
[ Person1 ] --> [ Address: Mumbai ]

Shallow Copy:
[ Person2 ] --> [ Address: Mumbai ]  (Dono ka shared Address object)
```

* Shallow Copy mein **Person1** aur **Person2** ka **same Address object** hota hai.
* Agar aap `Person2` ke `Address` ko change karenge, toh `Person1` ka address bhi change hoga, kyunki **same reference** share ho raha hai.

#### Example (Output after change):

```plaintext
Person1 Address: Delhi
Person2 Address: Delhi
```


* **Shallow Copy** mein object ka ek naya reference banaya jata hai, lekin original object ke nested objects ya complex data structures (e.g., arrays, lists) ka reference copy hota hai.
* Iska matlab hai ki agar nested object ko modify kiya jaye, toh dono objects mein change dikhai dega.

#### Example of Shallow Copy:

```java
class Person implements Cloneable {
    String name;
    Address address;

    public Person(String name, Address address) {
        this.name = name;
        this.address = address;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone(); // Shallow copy
    }

    @Override
    public String toString() {
        return "Person{name='" + name + "', address=" + address + "}";
    }
}

class Address {
    String city;

    public Address(String city) {
        this.city = city;
    }

    @Override
    public String toString() {
        return "Address{city='" + city + "'}";
    }
}

public class ShallowCopyExample {
    public static void main(String[] args) throws CloneNotSupportedException {
        Address address = new Address("Mumbai");
        Person person1 = new Person("John", address);

        // Shallow copy of person1
        Person person2 = (Person) person1.clone();

        // Modify the address in person2
        person2.address.city = "Delhi";

        System.out.println("Person 1: " + person1); // Address will be updated
        System.out.println("Person 2: " + person2);
    }
}
```

#### Output:

```
Person 1: Person{name='John', address=Address{city='Delhi'}}
Person 2: Person{name='John', address=Address{city='Delhi'}}
```

### Explanation:

* **Shallow Copy** mein `person2` ka address `person1` ke address ko refer karta hai.
* Jab `person2` ka address modify kiya gaya, toh change `person1` mein bhi reflect hua, kyunki dono objects ek hi address ko refer kar rahe hain.

---


### **2. Deep Copy**

```plaintext
Original Person:
[ Person1 ] --> [ Address: Mumbai ]

Deep Copy:
[ Person2 ] --> [ Address: Delhi ]  (Independent Address object)
```

* Deep Copy mein, **Person2** ke liye ek naya `Address` object banaya jata hai.
* Agar aap `Person2` ke `Address` ko change karenge, toh **Person1** ka address unaffected rahega.

#### Example (Output after change):

```plaintext
Person1 Address: Mumbai
Person2 Address: Delhi
```


* **Deep Copy** mein original object ka pura structure duplicate kiya jata hai, including its nested objects.
* Dono objects completely independent hote hain. Kisi ek object ko modify karne par dusre object par koi asar nahi hota.

#### Example of Deep Copy:

```java
class Person implements Cloneable {
    String name;
    Address address;

    public Person(String name, Address address) {
        this.name = name;
        this.address = address;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        // Perform deep copy
        Person cloned = (Person) super.clone();
        cloned.address = new Address(this.address.city); // Clone nested object
        return cloned;
    }

    @Override
    public String toString() {
        return "Person{name='" + name + "', address=" + address + "}";
    }
}

class Address {
    String city;

    public Address(String city) {
        this.city = city;
    }

    @Override
    public String toString() {
        return "Address{city='" + city + "'}";
    }
}

public class DeepCopyExample {
    public static void main(String[] args) throws CloneNotSupportedException {
        Address address = new Address("Mumbai");
        Person person1 = new Person("John", address);

        // Deep copy of person1
        Person person2 = (Person) person1.clone();

        // Modify the address in person2
        person2.address.city = "Delhi";

        System.out.println("Person 1: " + person1); // Address will not change
        System.out.println("Person 2: " + person2);
    }
}
```

#### Output:

```
Person 1: Person{name='John', address=Address{city='Mumbai'}}
Person 2: Person{name='John', address=Address{city='Delhi'}}
```

### Explanation:

* **Deep Copy** mein `person2` ka address completely independent hai `person1` ke address se.
* Jab `person2` ka address modify kiya gaya, toh `person1` ka address unaffected raha.

---



### **Difference Samjhein:**

1. **Shallow Copy** :

* Same `Address` object dono ke saath share hota hai.
* Kisi ek ka address change karne se dono pe asar padega.

1. **Deep Copy** :

* Har `Person` ka apna independent `Address` object hota hai.
* Kisi ek ka address change karne se doosre pe koi asar nahi hoga.


### **Comparison Between Shallow and Deep Copy**

| Feature                  | Shallow Copy                               | Deep Copy                          |
| ------------------------ | ------------------------------------------ | ---------------------------------- |
| **Nested Objects** | References are copied                      | Entire objects are copied          |
| **Independence**   | Objects are dependent on each other        | Objects are completely independent |
| **Performance**    | Faster to create                           | Slower due to object duplication   |
| **Use Case**       | When nested object changes aren't critical | When full independence is needed   |

---

### **Summary in Hinglish** :

* **Shallow Copy** : Bas outer object ka copy hota hai, andar ke objects ka reference copy hota hai (change dono mein dikhega).
* **Deep Copy** : Har cheez ka naya object banta hai (change ek mein hoga, dusre mein nahi).

Agar aur detail chahiye ya kisi part mein confusion ho, toh batao! 😊

```

class Address implements Cloneable {
	String city;
}
```

```
class Person implements Cloneable {
	String name;
	Address address;	// Method for shallow copy
	protected Person shallowCopy() throws CloneNotSupportedException {
		return (Person) super.clone(); // Only copies reference of address
	}	// Method for deep copy
	protected Person deepCopy() throws CloneNotSupportedException {
		Person deepCopyPerson = (Person) super.clone(); // Shallow copy of Person
		deepCopyPerson.address = new Address(); // Create new Address object for deep copy
		deepCopyPerson.address.city = this.address.city; // Copy the value of city
		return deepCopyPerson;
	}
}
```

```
public class CopyExample {
	public static void main(String[] args) throws CloneNotSupportedException {
		// Original person object
		Person originalPerson = new Person();
		originalPerson.name = "Alice";
		originalPerson.address = new Address();
		originalPerson.address.city = "New York";		// Shallow copy of person
		Person shallowCopyPerson = originalPerson.shallowCopy();		// Deep copy of person
		Person deepCopyPerson = originalPerson.deepCopy();		// Modify the address in shallow copy
		shallowCopyPerson.address.city = "Los Angeles";		// Modify the address in deep copy
		deepCopyPerson.address.city = "Chicago";		// Output results to show difference between shallow and deep copies
		System.out.println("Original Person City: " + originalPerson.address.city); // Los Angeles
		System.out.println("Shallow Copy Person City: " + shallowCopyPerson.address.city); // Los Angeles
		System.out.println("Deep Copy Person City: " + deepCopyPerson.address.city); // Chicago
	}
}
```

```
public class Team {
	String teamName;	public Team(String teamName) {
		this.teamName = teamName;
	}	// Deep copy method for Team
	public Team clone() {
		return new Team(this.teamName);
	}}
```

```
class FootballPlayer implements Cloneable {
	String name;
	String position;
	Team team;	public FootballPlayer(String name, String position, Team team) {
		this.name = name;
		this.position = position;
		this.team = team;
	}	@Override
	protected FootballPlayer clone() throws CloneNotSupportedException {
		FootballPlayer deepClone = (FootballPlayer) super.clone(); // Perform shallow copy
		deepClone.team = this.team.clone(); // deep copy
		return deepClone;
	}
}
```

```
public class JavaClone {
	public static void main(String[] args) throws CloneNotSupportedException {
        // Original Player
        Team originalTeam = new Team("Real Madrid");
        FootballPlayer originalPlayer = new FootballPlayer("Ronaldo", "Striker", originalTeam);        // Clone the Player
        FootballPlayer clonedPlayer = originalPlayer.clone();        // Modify the cloned object's team name
        clonedPlayer.team.teamName = "Manchester United";        // Display details
        System.out.println("Original Player Name: " + originalPlayer.name);
		System.out.println("Original Player Position: " + originalPlayer.position);
		System.out.println("Cloned Player Name: " + clonedPlayer.name);
		System.out.println("Cloned Player Position: " + clonedPlayer.position);
        System.out.println("Original Player Team: " + originalPlayer.team.teamName); // Real Madrid
        System.out.println("Cloned Player Team: " + clonedPlayer.team.teamName);   // Manchester United
    }
}
```
