> 1. In words, list 3 reasons why structs are different from resources.

- Structs can be copied , resources cannot be copied.
- You have to DO something with each resource, they cannot be left "hanging".
- Structs can be created anywhere, resources can only be created inside a contract.

> 2. Describe a situation where a resource might be better to use than a struct.

When representing an NFT via code, where security and clarity are of utmost importance.

> 3. What is the keyword to make a new resource?

create

> 4. Can a resource be created in a script or transaction (assuming there isn't a public function to create one)?

No, only inside a contract.

> 5. What is the type of the resource below?

Jacob

> 6.

    pub contract Test {

        // Hint: There's nothing wrong here ;)
        pub resource Jacob {
            pub let rocks: Bool
            init() {
                self.rocks = true
            }
        }

        pub fun createJacob(): @Jacob { // there is 1 here: Resource should have @ modifier: @Jacob
            let myJacob <- create Jacob() // there are 2 here: Needs <- instead of =, and needs 'create' keyword
            return <- myJacob // there is 1 here: resource needs explicitly moving via '<-' cannot just return resource.
        }
    }
