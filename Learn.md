# Shadowing Inherited State Variables

Unlike functions, state variables cannot be overridden by re-declaring it in the child contract.

Let's write a parent contract first:

```
contract Parent {
    string public name = "Contract Parent";

    function getName() public view returns (string memory) {
        return name;
    }
}
```

Let's learn how to correctly override inherited state variable `name`.

## Overriding Inherited State Variables incorrectly

- Shadowing is disallowed in Solidity 0.6. This will not compile

```
contract B is Parent {
    string public name = "Contract B";
}
```

## Overriding Inherited State Variables correctly

- This is the correct way to override inherited state variables.

```
contract Child is Parent {
    constructor() {
        name = "Contract Child";
    }

}
```

Hit `Run` to test if it works.
You should see `Contract Child` in the `name()` output.
