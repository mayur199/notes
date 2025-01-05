**HashMap** ek Java collection class hai jo key-value pairs ko store karti hai.

Isme hum data ko unique keys ke saath store karte hain, aur har key ko ek value assign karte hain.

 Jab hum kisi key se value access karte hain, toh HashMap fast tarike se value ko find karta hai.

### Key Features:

1. **Key-Value Pair** : Data ko key aur value ke roop mein store kiya jata hai.
2. **Unique Keys** : Har key unique hoti hai.
3. **No Order** : HashMap elements ko koi specific order mein store nahi karti.
4. **Null Keys & Values** : Aap ek key ya value ko `null` bhi de sakte hain.

### Example:

```java
import java.util.HashMap;

public class HashMapExample {
    public static void main(String[] args) {
        // HashMap create karna
        HashMap<String, String> capitalCities = new HashMap<>();

        // Key-Value pairs add karna
        capitalCities.put("India", "New Delhi");
        capitalCities.put("USA", "Washington, D.C.");
        capitalCities.put("Japan", "Tokyo");

        // Value access karna key ke through
        System.out.println("India ka capital: " + capitalCities.get("India"));
        System.out.println("USA ka capital: " + capitalCities.get("USA"));

        // HashMap ka size
        System.out.println("Total entries: " + capitalCities.size());

        // Ek key ko remove karna
        capitalCities.remove("Japan");

        // HashMap ko print karna
        System.out.println("HashMap after removal: " + capitalCities);
    }
}
```

### Output:

```
India ka capital: New Delhi
USA ka capital: Washington, D.C.
Total entries: 3
HashMap after removal: {India=New Delhi, USA=Washington, D.C.}
```

### Explanation (Hinglish):

* `put()` method se hum key-value pairs ko add karte hain.
* `get()` method se hum key ke corresponding value ko access karte hain.
* `remove()` method se hum kisi key ko remove kar sakte hain.
* `size()` method se HashMap ki size (number of entries) ko jaan sakte hain.

Agar aapko **HashMap** ke elements ko loop ke through access karna hai, toh aap **for-each loop** ya **Iterator** ka use kar sakte hain. Main dono tarike aapko samjhata hoon.

### 1. **For-Each Loop (Entry Set)**

HashMap ko iterate karte waqt **entrySet()** ka use karna sabse efficient tareeka hai. Isme aap har key-value pair ko access kar sakte ho.

```java
import java.util.HashMap;
import java.util.Map;

public class HashMapLoopExample {
    public static void main(String[] args) {
        HashMap<String, String> capitalCities = new HashMap<>();
  
        capitalCities.put("India", "New Delhi");
        capitalCities.put("USA", "Washington, D.C.");
        capitalCities.put("Japan", "Tokyo");
  
        // Using for-each loop to iterate over HashMap
        for (Map.Entry<String, String> entry : capitalCities.entrySet()) {
            System.out.println("Country: " + entry.getKey() + ", Capital: " + entry.getValue());
        }
    }
}
```

### Output:

```
Country: India, Capital: New Delhi
Country: USA, Capital: Washington, D.C.
Country: Japan, Capital: Tokyo
```

### Explanation:

* `capitalCities.entrySet()` se aapko HashMap ke saare key-value pairs milte hain.
* `Map.Entry<String, String>` ka use karke hum key aur value ko retrieve karte hain.

---

### 2. **For-Each Loop (Key Set)**

Agar aapko sirf keys ko access karna hai, toh aap `keySet()` ka use kar sakte hain.

```java
import java.util.HashMap;

public class HashMapLoopExample {
    public static void main(String[] args) {
        HashMap<String, String> capitalCities = new HashMap<>();
    
        capitalCities.put("India", "New Delhi");
        capitalCities.put("USA", "Washington, D.C.");
        capitalCities.put("Japan", "Tokyo");

        // Looping through keys
        for (String key : capitalCities.keySet()) {
            System.out.println("Country: " + key + ", Capital: " + capitalCities.get(key));
        }
    }
}
```

### Output:

```
Country: India, Capital: New Delhi
Country: USA, Capital: Washington, D.C.
Country: Japan, Capital: Tokyo
```

### Explanation:

* `capitalCities.keySet()` se aapko HashMap ke saare keys milte hain.
* `capitalCities.get(key)` se hum har key ke corresponding value ko access karte hain.

---

### 3. **Iterator (Advanced)**

Agar aapko Iterator ka use karna hai, toh aap kuch is tarah se loop laga sakte hain:

```java
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;

public class HashMapLoopExample {
    public static void main(String[] args) {
        HashMap<String, String> capitalCities = new HashMap<>();
    
        capitalCities.put("India", "New Delhi");
        capitalCities.put("USA", "Washington, D.C.");
        capitalCities.put("Japan", "Tokyo");
    
        // Using Iterator to loop through HashMap
        Iterator<Map.Entry<String, String>> iterator = capitalCities.entrySet().iterator();
    
        while (iterator.hasNext()) {
            Map.Entry<String, String> entry = iterator.next();
            System.out.println("Country: " + entry.getKey() + ", Capital: " + entry.getValue());
        }
    }
}
```

### Output:

```
Country: India, Capital: New Delhi
Country: USA, Capital: Washington, D.C.
Country: Japan, Capital: Tokyo
```

### Explanation:

* `entrySet().iterator()` se aap HashMap ke saare entries ko iterate karte hain..
