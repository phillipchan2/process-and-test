# process-and-test.js
A JS function that allows for a streamlined process that allows for multiple tests to be passed along its process.

![alt tag](https://raw.githubusercontent.com/ryanschuhler/lrdcom-recipes/f5bb3987e2d00d4ee9729f039a55b7452da3ba31/6.2.x/csv-to-hubspot/assets/CSV-Hubspot-Architecture.png)

Often, we need to simulataneously process and a file and test it along the way to ensure the integrity of the file. This module should help that.

If it's good, it will return the final process of the file.
If not, it should return the error message set for that step.

### Usage
1) Init our object:

```
var someProcess = new processAndTest();
```

2) Add in each step along with the tests we want to attach to that step. See the options in the constructor:

```
someProcess.newProcess({
    action: function() {
        // whatever we want to do with our data-as long as we return it.
        return data;
    },
    tests: [
        test1,
        test2
    ],
    errorMessage: "The error message given if this fails the test."
});
```

3) Run the test with the `run()` method.

```
someProcess.run();
```

**Results**
What returns is an object with 1) the result of the tests 2) data OR error message

```
var results = someProcess.run();
results.pass // returns true or false
results.data // returns either the finished product OR the error message.
```
