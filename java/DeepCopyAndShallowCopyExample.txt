class Address implements Cloneable {
	String city;
}


class Person implements Cloneable {
	String name;
	Address address;

	// Method for shallow copy
	protected Person shallowCopy() throws CloneNotSupportedException {
		return (Person) super.clone(); // Only copies reference of address
	}


	// Method for deep copy
	protected Person deepCopy() throws CloneNotSupportedException {
		Person deepCopyPerson = (Person) super.clone(); // Shallow copy of Person
		deepCopyPerson.address = new Address(); // Create new Address object for deep copy
		deepCopyPerson.address.city = this.address.city; // Copy the value of city
		return deepCopyPerson;
	}
}

public class CopyExample {
	public static void main(String[] args) throws CloneNotSupportedException {
		// Original person object
		Person originalPerson = new Person();
		originalPerson.name = "Alice";
		originalPerson.address = new Address();
		originalPerson.address.city = "New York";

		// Shallow copy of person
		Person shallowCopyPerson = originalPerson.shallowCopy();

		// Deep copy of person
		Person deepCopyPerson = originalPerson.deepCopy();

		// Modify the address in shallow copy
		shallowCopyPerson.address.city = "Los Angeles";

		// Modify the address in deep copy
		deepCopyPerson.address.city = "Chicago";

		// Output results to show difference between shallow and deep copies
		System.out.println("Original Person City: " + originalPerson.address.city); // Los Angeles
		System.out.println("Shallow Copy Person City: " + shallowCopyPerson.address.city); // Los Angeles
		System.out.println("Deep Copy Person City: " + deepCopyPerson.address.city); // Chicago
	}
}

public class Team {
	String teamName;

	public Team(String teamName) {
		this.teamName = teamName;
	}

	// Deep copy method for Team
	public Team clone() {
		return new Team(this.teamName);
	}

}
class FootballPlayer implements Cloneable {
	String name;
	String position;
	Team team; 

	public FootballPlayer(String name, String position, Team team) {
		this.name = name;
		this.position = position;
		this.team = team;
	}

	@Override
	protected FootballPlayer clone() throws CloneNotSupportedException {
		FootballPlayer deepClone = (FootballPlayer) super.clone(); // Perform shallow copy
		deepClone.team = this.team.clone(); // deep copy
		return deepClone;
	}

}
public class JavaClone {
	public static void main(String[] args) throws CloneNotSupportedException {
        // Original Player
        Team originalTeam = new Team("Real Madrid");
        FootballPlayer originalPlayer = new FootballPlayer("Ronaldo", "Striker", originalTeam);

        // Clone the Player
        FootballPlayer clonedPlayer = originalPlayer.clone();

        // Modify the cloned object's team name
        clonedPlayer.team.teamName = "Manchester United";

        // Display details
        System.out.println("Original Player Name: " + originalPlayer.name);
		System.out.println("Original Player Position: " + originalPlayer.position);
		System.out.println("Cloned Player Name: " + clonedPlayer.name);
		System.out.println("Cloned Player Position: " + clonedPlayer.position);
        System.out.println("Original Player Team: " + originalPlayer.team.teamName); // Real Madrid
        System.out.println("Cloned Player Team: " + clonedPlayer.team.teamName);   // Manchester United
    }
}
