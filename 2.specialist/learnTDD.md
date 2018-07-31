# Learn Test-Driven Development

Test-driven development is a software development practice that organizes work as very short cycles of design, test, and implementation.

## An example of automated testing

TDD requires the use of automated software testing tools. Here is a simplified mockup of an automated test. (This is similar to the actual testing logic, written in `mocha.js`, that is used to test our applications. Don't worry about the syntax; just try to follow the concepts.)

```
context("when a record is read from the database", function() {           // 1
  it("should include the expected 'description' value", function(done) {  // 2
    expectedDescription = 'some value invented for testing';

    record.read(verifyResults);                                           // 3

    function verifyResults(record) {
      should.exist(record.description);                                   // 4
      record.description.should.equal(expectedDescription);               // 5
      done(); // all assertions were true
    }
  });
});
```

The automated testing tools allow us to:
1. describe a `context` for the test, in English
2. use `it("should ..." ` to define the test by describing the expected behavior, in English
3. call the code under test, and say how to check the results (Here we are testing the `record.read()` function, and using the `verifyResults()` function to check its behavior.)
4. check that the record has a `description` field
5. check that the record's description has the value we expect

The statements marked 4 and 5 above are *assertions*. If an assertion evaluates to `false`, the test immediately fails and stops. If an assertion evaluates to `true`, the test continues. If the test run reaches `done();`, that means that all assertions were `true`, and the test has passed.

## How to do test-driven development 

The simplest way to begin practicing TDD is to conform to the following simple rules when developing new software features.

1. Write a single automated test, similar to the example above.
2. Run this new test. It *should* fail, because it is testing something that has not yet been built.
3. Write the smallest amount of application code possible to make the test pass.
4. Run the new test again. If it still fails, return to step 3.
5. Now that the new test is passing, run *all* automated tests. None of these tests were failing when you started step 1, and that should still be true. If any are failing, you have broken something, which you must investigate and repair.
6. If the new feature is not yet complete, return to step 1.

This process is important because:
- the automated tests are a precise statement of expected program behavior
- it is quick and easy to show that the software satisfies this expected behavior
- code is checked often, in small amounts, so we are constantly returning to "all correct" behavior
- it is safe to make changes without fear of breaking anything

In some ways, this amounts to writing the logic twice. But this extra work is highly valuable, much like double-entry accounting where all debits and credits must balance. The software can now be thoroughly tested at the click of a button, as often and as many times as we want.

## Using tests as human communication

Of course, TDD is not magic. Suppose some new code passes a test, but the test logic does not correctly describe the required behavior. Maybe the users expect the database record in our example will have a field called 'Product Description', not 'description'. The test and the feature code "agree", but they are *both wrong*.

We can reduce the probabilty of these problems by involving more people. The process described above implies that one person writes both the test code and the code "under test" (the code being tested). But there is value in having two programmers collaborate. Suppose that Alice and Bob collaborate to add the next feature in our example. Together, they add the following to the example `context` above.

```
  it("should include the expected 'price' value", function(done) { 

    record.read(verifyResults);                          

    function verifyResults(record) {
      done(); // all assertions were true
    }
  });
```

They have completed *part* of step 1 in our TDD process. At this point, both programmers agree that a record should contain some particular value for 'price' when it is read from the database. They briefly part ways to work independently. Alice completes step 1 by adding assertions before the `done()` call in the test above, so that the test fully verifies the expected outcome. She also performs step 2 (it is tempting to skip this, but an incorrect assertion can make a test pass in all cases, which means it really is not testing anything). Meanwhile, Bob performs step 3 by adding code to the `record.read()` function so that it behaves as expected.

Alice and Bob combine their code and perform step 4. When the new test passes, we can be sure that two different people understood the expected behavior in the same way, and independently captured it in equivalent logic. This is a much stronger test.

## Pending tests as design documentation 

Another technique for human communication is to use pending tests to specify detailed design decisions.

```
  it("should calculate the sales tax"); // a pending test neither passes nor fails
```

The example above says that the code under test should calculate the sales tax, but it does not attempt to test that. The automated test tools will not mark this test as passing or as failing; it is marked "pending" instead.

This can be useful to document a high-level understanding of expected behavior. Suppose that a programmer is uncertain about which behaviors should be implemented by the feature she is assigned. A good approach would be to write a set of pending tests as a best guess of the expected behavior. This documentation can be reviewed by managers or by customers (with some help from us) so that everyone has a common understanding of what we want before investing time in specifying how it will be done.
