# Advanced

The advanced page can be left with all of it's defaults. Only change these settings where necessary.

1. Enter the time that a scroll window should run for large queries in the Scroll Window.
2. If you want to limit the number of documents that are retrieved per Scroll Request enter it within Scroll Size.
3. Define the maximum number of Retrieval operations that can be run at the same time in Retrieval Max Degree of Parallelism.
4. Define the maximum number of operations that can be run at the same time in Copy Max Degree of Parallelism.
5. Control the amount of work that can be queued at each step of a migration. Enter the number in Bounded Capacity.
   * Lower numbers will use less memory but could cause steps to run out of work.
   * Higher numbers will use more memory but all steps will likely always be running.

<figure><img src="../../../../.gitbook/assets/image (306).png" alt="" width="563"><figcaption></figcaption></figure>

#### Errors

1. Check Enable Circuit breaker to stop a migration when the error occurs multiple times.
2. Enter the number of acceptable errors in Error Threshold.
3. If you want a stop a migration due to file exceptions, check File Exceptions Trigger Circuit Breaker.
   * Circuit breaker must be enabled for this to work.
4. Enter the amount of time that can elapse before a file exception stops a migration.
