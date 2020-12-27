# Managing Processes

## Kill

```bash
    kill -SIGKILL { PID }
    kill -9 { PID }
```

NOTE: **9** is the numerical notation for **SIGKILL**.

**kill** combined with the *signal kill* tag kills a process by the specified PID. A user is only able to kill his/her process, unless sudo is used. The **kill** command is actually used to send signals to a process; it is up to the process to understand the signal being sent and react accordingly. As a result, it is posible a program many not stop despite sending the SIGKILL command.

## System Control

```bash
    sudo systemctl start gdm
    sudo systemctl stop gdm
```
**system control:** Systems running on *systemd* can use the **systemctl** keyword, which allows for the user to start and stop processes much easier. The above commands start and stop the graphical display manager.

## Niceness

```bash
    nice -n { niceness } { instruction }
    renice -n { niceness } { PID }
```

**nice** sets the niceness value for terminal commands, while **renice** sets the niceness value for existing processes. Default niceness value is 0.

**Value Range**: [-19, 20]

## Background & Foreground

```bash
    { instruction } &

    bg %{ job-ID }
    fg %{ job-ID }

    bg %+
    fg %-
```

A command can be executed in the background by including an ampersand at the end. Additionally, the **background** command resumes the specified job in the background. To bring a command to the foreground, use the **foreground** command. **%-** refers to the previous job, while **%+** refers to the current job.

**NOTE:** While on the terminal, CTRL-Z suspends a foreground job while CTRL-C terminates it.

## At, At Queue & At Remove

```bash
    at { time } { script-filename }
    at { time }
    atq
    at -c { job-ID }
    atrm { job-ID }
```

**at** is useful for scheduling one-time tasks. Either a script location can be specified, or the user will be provided with an editor to type in commands. **at queue** shows processes waiting to be executed at their respective job IDs. The job ID of a process can then be used with **at** and the *command* tag to view its commands. Lastly, a job can be removed with **at remove**. 

**Examples of Specifying Time for 'at':**
* now + 30 minutes
* now + 3 weeks
* 2:30 PM October 18 2020

## CRON Table

```bash
    crontab -e
```

CRON is a time-based scheduling utility program. **CRON Table** with the *editor* tag will launch an editor to edit this table. Each line will contain the following fields:

| Field        | Values           |
| ------------ | ---------------- |
| Minute       | 0-59             |
| Hour         | 0-23             |
| Day of Month | 1-31             |
| Month        | 1-12             |
| Day of Week  | 0-6 (0 = Sunday) |
| Command      |                  |

**Examples:**
* **\* \* \* \* \* ~/script.sh** - Will execute *script.sh* every minute of every hour of every day of the month, and every month and every day in the week. 
  
* **30 08 10 06 1-5 ~/script.sh** - Will execute script.sh at 8:30 a.m. 10-June, as long as it is a weekday.

If the computer isn't functioning during the time period specified, a program called **anacron** will perform the task once the computer is functioning again.