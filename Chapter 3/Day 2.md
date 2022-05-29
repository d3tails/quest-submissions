> For today's quest, you'll have 1 large quest instead of a few little ones.
> 
> Write your own smart contract that contains two state variables: an array of resources, and a dictionary of resources. Add functions to remove and add to each of them. They must be different from the examples above.

    // SeedBank stores seeds, each seed has a unique ID and a name.
    pub contract SeedBank {

        pub var seedsArray: @[Seed]
        pub var seedsDictionary: @{UInt64: Seed}

        pub resource Seed {

            pub let id: UInt64
            pub let name: String

            init(_id: UInt64, _name: String) {
                self.id = _id
                self.name = _name
            }

        }

        // Add to array
        pub fun addSeedToArray(_seed: @Seed) {
            self.seedsArray.append(<- _seed)
        }

        // Remove from array
        pub fun removeSeedFromArray(_index: UInt64) : @Seed {
            return <- self.seedsArray.remove(at: _index)
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
            self.seedsArray <- []
            self.seedsDictionary <- {}
        }

    }
