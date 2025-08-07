# Scheduling

## Introduction

Choose when and how regularly a job is run. All times are in Coordinated Universal Time (UTC).

### Periodically

Choose to run this job at regular occurring intervals using a cron expression.

1. Enter your Cron expression into Schedule Cron.
   * Create your Cron expression using [www.cronmaker.com](https://www.cronmaker.com/)
2. You can create a timeout to stop a job that runs for an excessive amount of time. By default this will be -1 which applies no limit.
   * Applying a timeout can ensure unnecessary jobs aren't taking up processing power

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-02-13 at 16.27.39.png" alt=""><figcaption></figcaption></figure>

### Timetable

Choose Timetable to Set the time and day over a 7 day period to schedule this job. These schedules will run the same time every week until manually stopped.

1. Selecting a square from the grid will invert its setting. Green is active and the job will run during this time, white inactive and it will not run.
2. You can choose many or as few active squares.
   * Selecting Always Run will mark all the squares as active. This will give the most accurate representation but will use more processing capabilities.
   * Selecting Outside Working Hours will set Mon - Fri 8am-6pm as inactive. This will reduce any issues to users as processing power can be contained.
   * Toggle inverts the selection switching anything from active to inactive and vice versa.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-02-13 at 16.29.45.png" alt=""><figcaption></figcaption></figure>

### Manually Run

Choose to ensure this job runs only when started by an Admin. This option means the job will run as and when started from the configurations pages.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-02-13 at 16.31.16.png" alt=""><figcaption></figcaption></figure>

### Disabled

Disabling this from scheduling means it can not be run manually.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-02-13 at 16.31.50.png" alt=""><figcaption></figcaption></figure>

