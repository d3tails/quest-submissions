>Explain why we wouldn't call changeGreeting in a script.

Scripts can only read data from a contract, transactions are needed to change data.

>What does the AuthAccount mean in the prepare phase of the transaction?

AuthAccount is a reference to the account signing the tranaction.

>What is the difference between the prepare phase and the execute phase in the transaction?

- Prepare phase: Getting information from the AuthAccount (transaction signer).
- Execute phase: Interact with and change data/state of the smart contract.

>This is the hardest quest so far, so if it takes you some time, do not worry! I can help you in the Discord if you have questions.
> - Add two new things inside your contract:
>   - A variable named myNumber that has type Int (set it to 0 when the contract is deployed)
>   - A function named updateMyNumber that takes in a new number named newNumber as a parameter that has type Int and updates myNumber to be newNumber

![image](https://user-images.githubusercontent.com/104716561/168460864-fd3b3dd8-2ae7-43bd-b9e3-19552b3d2cef.png)

> - Add a script that reads myNumber from the contract
> - Add a transaction that takes in a parameter named myNewNumber and passes it into the updateMyNumber function. Verify that your number changed by running the script again.

![image](https://user-images.githubusercontent.com/104716561/168460907-3de7f253-1e01-44c2-ae8a-52b215628a98.png)

![image](https://user-images.githubusercontent.com/104716561/168460919-57094645-8186-432c-8993-de3d1ce99093.png)
