### Question #1

What does `SOLID` Stand for ? explain the basic idea

<details>
<summary>Answer</summary>

`SOLID` is a mnemonic acronym that stands for five principles of object-oriented design and programming

<br>

1. **Single Responsibility Principle (SRP)**: The single responsibility principle states that a class or module should have only one reason to change. This means that a class should have a single, well-defined responsibility, and all of its methods and properties should be related to that responsibility. Adhering to this principle can help to make a system more modular and easier to understand and maintain, as it reduces the number of potential interactions between different parts of the system.

_example_:

The user account class has a single responsibility: managing user accounts. It has properties for the user's name, email address, and password, and methods for signing in and signing out. It does not have any responsibility for sending emails or performing any other unrelated tasks.

<br>

2. **Open-Closed Principle (OCP)**: The open-closed principle states that software entities (such as classes, modules, functions, etc.) should be open for extension but closed for modification. This means that you should be able to add new functionality to a class without changing its existing code, by extending the class or implementing new classes that conform to the same interface. Adhering to this principle can help to make a system more flexible and easier to maintain, as it reduces the need to modify existing code when adding new features.

_example_:

Suppose you want to add a new feature to the application that allows users to sign in using their social media accounts (such as Facebook or Google). You could create a new class that extends the user account class and implements the necessary additional behavior, without modifying the existing user account class. This would allow you to add new functionality to the system without changing the existing code, which helps to adhere to the open-closed principle.

```Javascript
class UserAccount {
  // UserAccount code
}

class SocialMediaUserAccount extends UserAccount {
  constructor(name, email, password, socialMediaType) {
    super(name, email, password);
    this.socialMediaType = socialMediaType;
  }

  signIn() {
    // code to sign in the user using their social media account goes here
  }
}
```

<br>

3. **Liskov Substitution Principle (LSP)**: The Liskov substitution principle states that subtypes must be substitutable for their base types. This means that if a class is a subtype of another class, it should be able to be used in the same way as the base class without causing any problems. Adhering to this principle can help to ensure that a system is more predictable and easier to understand and maintain, as it reduces the risk of unexpected behavior when using subtypes in place of their base types.

_example_:

Suppose you have code that depends on the user account class and expects it to have a signIn() method. If you create a new class that extends the user account class and implements the signIn() method, you should be able to use an instance of the new class in the same way as an instance of the user account class without causing any problems. This helps to adhere to the Liskov substitution principle.

```JavaScript
function doSomethingWithUserAccount(userAccount) {
  userAccount.signIn();
  // do other things with the user account
}

const userAccount = new UserAccount('John', 'john@example.com', 'password');
doSomethingWithUserAccount(userAccount);

const socialMediaUserAccount = new SocialMediaUserAccount('John', 'john@example.com', 'password', 'facebook');
doSomethingWithUserAccount(socialMediaUserAccount);
```

<br>

4. **Interface Segregation Principle (ISP)**: The interface segregation principle states that clients should not be forced to depend on interfaces they do not use. This means that a class should not be forced to implement methods that it does not need, as this can lead to unnecessary complexity and reduced flexibility. Adhering to this principle can help to make a system more modular and easier to understand and maintain, as it reduces the number of unnecessary dependencies between different parts of the system.

_example_:

Suppose you have an interface that defines the behavior of a user account, with methods for signing in and signing out. If you have a class that represents a user account that can be signed in using social media, it might only need to implement the signIn() method, as it does not support traditional email/password sign in. Adhering to the interface segregation principle, you would create a separate interface that defines only the signIn() method, and have the social media user account class implement that interface instead of the full user account interface.

```Javascript
interface UserAccountInterface {
  signIn(): void;
  signOut(): void;
}

interface SocialMediaUserAccountInterface {
  signIn(): void;
}

class UserAccount implements UserAccountInterface {
  // code from the previous example goes here
}

class SocialMediaUserAccount implements SocialMediaUserAccountInterface {
  // code from the previous example goes here
}
```

<br>

5. **Dependency Inversion Principle (DIP)**: The dependency inversion principle states that high-level modules should not depend on low-level modules. Both should depend on abstractions. This means that instead of depending on concrete implementations of low-level functionality, high-level modules should depend on abstractions that define the required behavior. This can help to make a system more flexible and easier to maintain, as it reduces the need to modify high-level modules when making changes to low-level modules.

_example_:

Suppose you have a high-level module that uses the user account class to sign users in and out of the application. Instead of depending on the concrete implementation of the user account class, the high-level module should depend on an abstraction that defines the required behavior. For example, you might create an interface that defines signIn() and signOut() methods, and have the user account class implement that interface. The high-level module would then depend on the interface rather than the concrete implementation, which helps to adhere to the dependency inversion principle.

<br>

</details>

<br>

[Back To Index](../index.md)
