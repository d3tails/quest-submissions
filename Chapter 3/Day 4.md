>1. Explain, in your own words, the 2 things resource interfaces can be used for (we went over both in today's content)

- Resource interfaces act as a template which defines variables and functions that a resource must implement.
- Resources that implement a resource interface only expose variables and functions that are defined in the corresponding interface.
  Anything else in the function that is not definied in the interface cannot be accessed.

>2. Define your own contract. Make your own resource interface and a resource that implements the interface.
>Create 2 functions. In the 1st function, show an example of not restricting the type of the resource and accessing its content.
>In the 2nd function, show an example of restricting the type of the resource and NOT being able to access its content.

    pub contract Lunch {

        pub resource interface ISandwich {
            pub var name: String
            pub var calories: Int
        }

        pub resource CheeseSandwich: ISandwich {

            pub var name: String
            pub var calories: Int
            pub var cheese: String

            init() {
                self.name = "Big ol sub"
                self.calories = 9000
                self.cheese = "brie"
            }

        }

        // Create 2 functions.
        // In the 1st function, show an example of not restricting the type of the resource and accessing its content.
        pub fun printCheese() {
            let sandwich: @CheeseSandwich <- create CheeseSandwich()
            log(sandwich.cheese)

            destroy sandwich
        }

        //  In the 2nd function, show an example of restricting the type of the resource and NOT being able to access its content.
        pub fun printCheese2() {
            let sandwich: @CheeseSandwich{ISandwich} <- create CheeseSandwich()
            log(sandwich.cheese) // ERROR 'member of restricted type is not accessible: cheese'

            destroy sandwich
        }

    }

>3. How would we fix this code?

    pub contract Stuff {

        pub struct interface ITest {
          pub var greeting: String
          pub var favouriteFruit: String

          pub fun changeGreeting(newGreeting: String): String // FIX: EXPOSE THE changeGreeting FUNCTION
        }

        // ERROR:
        // `structure Stuff.Test does not conform 
        // to structure interface Stuff.ITest`
        pub struct Test: ITest {
          pub var greeting: String
          pub var favouriteFruit: String // FIX: DEFINE OTHER VARIABLE FROM INTERFACE

          pub fun changeGreeting(newGreeting: String): String {
            self.greeting = newGreeting
            return self.greeting // returns the new greeting
          }

          init() {
            self.greeting = "Hello!"
            self.favouriteFruit = "Kumquat" // FIX: INITIALIZE OTHER VARIABLE FROM INTERFACE
          }
        }

        pub fun fixThis() {
          let test: Test{ITest} = Test()
          let newGreeting = test.changeGreeting(newGreeting: "Bonjour!") // ERROR HERE: `member of restricted type is not accessible: changeGreeting`
          log(newGreeting)
        }
    }
