
	
	What is JMod?
JMod (Java Module) file is a packaging format introduced in Java 9. It is used to bundle Java modules, which can contain compiled class files, native libraries, resources, and metadata. JMod files are primarily used for the following purposes:

Deployment: JMod files can be used to distribute Java modules for applications.
Native Libraries: They can include native code (e.g., DLLs or .so files) that can be used with Java applications.
Module Metadata: JMod files can store module information like dependencies and versions.
Why Use JMod?
Modularity: JMod helps in creating modular applications, making them easier to manage and deploy.
Dependency Management: It allows developers to manage dependencies more effectively.
Native Integration: JMod can package native libraries alongside Java classes, making it useful for applications that rely on native code.


	
	Step 1: Create a Simple Calculator Java Program file called Calculator.java.
	
	Step 2: Create a Module create a file named 
	module-info.java
	
	module com.simplecalculator {
    exports com.simplecalculator;
}

Java module ek logical unit hai jo aapke code ko organize karta hai aur encapsulate karta hai
Java module ko define karne ke liye ek special file hoti hai jise module-info.java kaha jata hai. Is file mein aap module ka naam define karte hain, aur jo packages doosre modules ke liye available honge, unhe exports karte hain.
--Is example mein:

--com.simplecalculator module ka naam hai.
--exports com.simplecalculator; ka matlab hai ki is module ka com.simplecalculator package doosre modules ke liye available hoga.

	Step 3: Compile the Calculator Program
	Open a terminal in the directory where your Calculator.java and module-info.java files are located.
    Create an out directory for compiled files.
	
	 mkdir out
     javac -d out module-info.java com\simplecalculator\Calculator.java
	
--> mkdir out

Ye command ek out naam ki nayi directory banati hai.
Purpose: Hum compiled classes ko out directory mein store karna chahte hain, taaki code compile karne ke baad, sabhi generated .class files uss folder mein rahein.

--> javac -d out module-info.java com\simplecalculator\Calculator.java

javac: Java compiler hai jo .java files ko compile karke .class files banaata hai.
-d out: Ye flag compiler ko batata hai ki jo compiled .class files generate karni hain, unhe out folder mein daal diya jaaye.
module-info.java: Ye file module ko define karti hai (jaise humne pehle discuss kiya tha), aur Java ko batati hai ki kis module mein kaunse packages aur classes hain.
com\simplecalculator\Calculator.java: Ye source file hai, jisme humne apna Calculator class likha hai.

	Step 4: Package the Program into a JMOD File
	mkdir jmods
	jmod create --class-path out --main-class com.simplecalculator.Calculator jmods/com.simplecalculator.jmod


-->mkdir jmods

Ye command ek nayi directory jmods banata hai, jo JMOD files ko store karega. JMOD file ek packaged module hoti hai jo apne classes, resources, aur configuration ko ek file mein store karti hai.

-->jmod create --class-path out --main-class com.simplecalculator.Calculator jmods/com.simplecalculator.jmod

jmod create: Ye command JMOD file banane ke liye use hoti hai.
--class-path out: Isse Java ko bataya jaata hai ki compiled class files out directory mein hain.
--main-class com.simplecalculator.Calculator: Ye flag specify karta hai ki com.simplecalculator.Calculator class main entry point hai, jise Java application ke execution ke liye use kiya jaayega.
jmods/com.simplecalculator.jmod: Ye destination path hai, jahan JMOD file create ki jaayegi. Yaha com.simplecalculator.jmod ek JMOD file ka naam hai.

    Step 5: Verify the Contents of the JMOD File
	jmod list jmods/com.simplecalculator.jmod

-->jmod list jmods/com.simplecalculator.jmod

 yeh command aapko JMOD file ke andar ke modules, packages, classes, aur resources dikhayegi.

	Step 6: Run the Module 
    java --module-path out -m com.simplecalculator/com.simplecalculator.Calculator

--> java --module-path out -m com.simplecalculator/com.simplecalculator.Calculator

java: Ye Java command hai, jo Java application ko run karne ke liye use hoti hai.

--module-path out: Ye flag Java ko batata hai ki modules ko locate karne ke liye out directory ka use karein. out directory wo location hai jahan aapne pehle Java code ko compile kiya tha aur modules ko store kiya hai.

Purpose: Aapne code ko module format mein compile kiya hai, aur is flag se Java ko bataya jaata hai ki compiled modules ko out directory mein dekhein.
-m com.simplecalculator/com.simplecalculator.Calculator:

-m: Ye flag Java ko batata hai ki module ko run karna hai.
com.simplecalculator: Ye aapka module name hai, jo aapne module-info.java mein define kiya tha.
com.simplecalculator.Calculator: Ye main class hai, jo module ke andar main entry point ko represent karti hai. Iska matlab hai ki Calculator class ka main method run hoga.


	//share jmods folder with other
	//java --module-path (path of jmods) -m com.simplecalculator/com.simplecalculator.Calculator