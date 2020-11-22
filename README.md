# KeyBinder
An easy to use, all-in-one class for a key-binding system in Unity.  
Supports input filtering (You can choose wich keys are valid for binding).
- **Content**
  - [Setup](#setup)
  - [Input Filtering System](#input-filtering-system)
  - [Properties](#properties)
  - [Methods](#methods)


# Setup
  
- First, create and initialize a KeyBinder.  
See [here](#input-filtering-system) about the input filtering system.  
Make sure you are using this class inside a MonoBehaviour
```csharp
KeyBinder keyBinder = new KeyBinder(); // A KeyBinder without input filtering
```
- Now, the most **IMPORTANT** thing:  
call the "Update()" method of the KeyBinder inside the Update() method of your MonoBehaviour
```csharp
private void Update()
{
  keyBinder.Update();
}
```
- Done. You're all set and can use the KeyBinder tool.
- See examples of use [here]()

# Examples
Do what the [Setup](#setup) section says first if you want these examples to work
- Let's say you have a KeyCode variable for the Jump action in your game.  
And you check if this KeyCode is pressed, and if it is, your charactar jumps.  
Now you want to let the player choose a key for Jump.
  - Create a method that takes a KeyCode and assigns it to the Jump key.
  ```csharp
  
  ```

# Input Filtering System
  - There's a **list** of "valid keys" inside a **KeyBinder** object
  - If the **list's empty**, the input filtering will **not work** (Every key the user will press will be valid)
  - If the filtering's is **working** it'll return the received key **only if** it is **inside that list**
  - You can **add keys** to the list with these methods:
  ```csharp
  AddValidKey(KeyCode)
  AddValidKeys(KeyCode[])
  AddValidKeys(List<KeyCoNde>)
  ```
  - You can also add them upon **initialization** with **constructors**
  ```csharp
  // No input, empty list, no filtering
  KeyBinder keyBinder = new KeyBinder();
  
  // Adds the key from the array you entered to the "valid keys list"
  KeyBinder keyBinder = new KeyBinder(KeyCode[]);
  
  // Adds the key from the list you entered to the "valid keys list"
  KeyBinder keyBinder = new KeyBinder(List<KeyCode>); 
  ```
  - Array of keys example:
  ```csharp
  KeyCode[] keysArray =
  {
    KeyCode.A, KeyCode.B, KeyCode.C, KeyCode.D, KeyCode.E, KeyCode.F,
    KeyCode.G, KeyCode.H, KeyCode.I
  }
  ```

## Properties
```csharp
LatestKey            // Returns the latest key the KeyBinder received.
IsActive             // Determines if the KeyBinder is currently checking for input.
KeyFilteringActive   // Determines if the KeyBinder will filter the input
```

## Methods
```csharp
Update() // Call this on Update() inside a MonoBehaviour

InputCheckingBeginSingle()
InputCheckingBeginContinuous()
InputCheckingCancel()
InputCheckingPause()
InputCheckingResume()

AddValidKey()
AddValidKeys()
ClearValidKeys()
```
