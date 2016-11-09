# Tasman

A TorqueScript testing framework for [T3D][] inspired by [Jasmine][].

 [T3D]: https://github.com/GarageGames/Torque3D
 [Jasmine]: https://jasmine.github.io/

# Example

```cs
// Declare a new test suite for MyObject.
test(MyObject);

// Set up before each test.
function MyObjectTests::before() {
   new ScriptObject(MyObject) {
      property = "foo";
   };
}

// And pull everything down afterwards!
function MyObjectTests::after() {
   MyObject.delete();
}

// A basic test - expect that the setup works correctly!
function MyObjectShould::exist() {
   expect(MyObject).toExist();
}

// More advanced matchers.
function MyObjectShould::have_a_property() {
   expect(MyObject.property).toHave(1).word();
   expect(MyObject.property).toEqual("foo");
   expect(MyObject.property).not().toEqual("bar");
}
```

The output should look something like:

 ![Tasman test output all passed](http://i.imgur.com/zkq1rab.png)

Now let's introuce a failure:

```cs
function MyObjectShould::do_something_silly() {
   expect(MyObject.property).toBeAVector(3);
}
```

And the output becomes:

 ![Tasman test output one failed](http://i.imgur.com/lM6IKfc.png)
