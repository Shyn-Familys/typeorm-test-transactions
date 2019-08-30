# TypeORM Test Transactions
Have you wanted to run tests on a project that uses TypeORM directly on the database and in parallel? A lot of the time we can't do this because artefacts and data from other tests can affect the result of our current tests. What usually happens, in this case, is that our tests become quite complicated when database entities are involved because we need to track exact entities. Our `count()` and other aggregations must have `where` clauses so that we don't see results from other tests that have already completed.

This library introduces a way to wrap tests in a transaction and automatically roll back the commits when the test ends. By doing this, you are able to run multiple tests concurrently and their data will not be seen by others.

You may argue that we should mock out the entities and not use a database at all. This is a valid point, but sometimes we want to test database constraints and the effects they can have on application logic.
