>1. Define your own contract that stores a dictionary of resources. Add a function to get a reference to one of the resources in the dictionary.

    // SeedBank stores seeds, each seed has a unique ID and a name.
    pub contract SeedBank {

        pub var seedsDictionary: @{UInt64: Seed}

        pub resource Seed {

            pub let id: UInt64
            pub let name: String

            init(_id: UInt64, _name: String) {
                self.id = _id
                self.name = _name
            }

        }

        // Get a reference to a seedDictionary resource.
        pub fun getSeedRef(_id: UInt64): &Seed {
            let ref = &self.seedsDictionary[_id] as &Seed
            return ref
        }

        // Add to dictionary
        pub fun addSeedToDict(_seed: @Seed) {
            self.seedsDictionary[_seed.id] <-! _seed 
        }

        // Remove from dictionary
        pub fun removeSeedFromDict(_id: UInt64): @Seed {
            var seed <- self.seedsDictionary.remove(key: _id) ?? panic("Panic: No seed with that ID")
            return <- seed
        }

        init() {
            self.seedsDictionary <- {
                25: <- create Seed(_id: 25,_name: "Lettuce"),
                69: <- create Seed(_id: 69,_name: "Sexyfruit"),
                42: <- create Seed(_id: 42,_name: "Apple")
            }
        }

    }

>2. Create a script that reads information from that resource using the reference from the function you defined in part 1.

![image](https://user-images.githubusercontent.com/104716561/170852545-f5b3118a-03c2-44e5-8a54-7b93a9b73f04.png)


>3. Explain, in your own words, why references can be useful in Cadence.

References provide access to resources, as opposed to having to manually pass them from place to place.
This could be useful when trying to read data from an NFT in a signer's account, as opposed to having to move the NFT out of the signer's account to read from it.
