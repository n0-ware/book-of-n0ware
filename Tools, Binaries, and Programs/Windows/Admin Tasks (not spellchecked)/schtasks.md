# schtasks
###### Tags[^1]
The `schtasks` taks is used to schedule programs or scripts to run at predetermined times or based on a trigger or set of triggers. Similar to the [crontab](../../Linux%20CLI%20Utilities/Fundamental%20Linux/crontab.md) that manages.

This command is highly complex, specifically when using it with triggers. See this link for more information. [schtasks manual page](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/schtasks-create)

## Syntax
```
C:\>schtasks /?

SCHTASKS /parameter [arguments]

Description:
    Enables an administrator to create, delete, query, change, run and
    end scheduled tasks on a local or remote system.

Parameter List:
    /Create         Creates a new scheduled task.

    /Delete         Deletes the scheduled task(s).

    /Query          Displays all scheduled tasks.

    /Change         Changes the properties of scheduled task.

    /Run            Runs the scheduled task on demand.

    /End            Stops the currently running scheduled task.

    /ShowSid        Shows the security identifier corresponding to a scheduled task name.

    /?              Displays this help message.

Examples:
    SCHTASKS
    SCHTASKS /?
    SCHTASKS /Run /?
    SCHTASKS /End /?
    SCHTASKS /Create /?
    SCHTASKS /Delete /?
    SCHTASKS /Query  /?
    SCHTASKS /Change /?
    SCHTASKS /ShowSid /?
```

Ran alone, it will list all currently scheduled tasks.

```
C:\>schtasks

Folder: \
TaskName                                 Next Run Time          Status
======================================== ====================== ===============
Adobe Acrobat Update Task                N/A                    Disabled
AdobeGCInvoker-1.0                       N/A                    Disabled
AMDAutoUpdate                            N/A                    Disabled
Avast Emergency Update                   1/31/2022 2:16:15 AM   Ready
BlueStacksHelper                         N/A                    Disabled
GoogleUpdateTaskMachineCore              N/A                    Disabled
GoogleUpdateTaskMachineUA                N/A                    Disabled
```

To view the help screen with a particular subcommand, provide it followed with `/?`

```
C:\>schtasks /create /?

SCHTASKS /Create [/S system [/U username [/P [password]]]]
    [/RU username [/RP password]] /SC schedule [/MO modifier] [/D day]
    [/M months] [/I idletime] /TN taskname /TR taskrun [/ST starttime]
    [/RI interval] [ {/ET endtime | /DU duration} [/K] [/XML xmlfile] [/V1]]
    [/SD startdate] [/ED enddate] [/IT | /NP] [/Z] [/F] [/HRESULT] [/?]
```
## Examples
Creating, listing, and running tasks is simple. For example, below we create a task that runs every day of the week at 5:30 PM starting the program *notepax.exe*. Following that, we can list it, then delete it, and verify it was deleted. 

For example, running notepad every day at 5 PM with a scheduled task. 

```
C:\>schtasks /create /sc weekly /d * /tn takenotes /tr notepad.exe /st 23:13
SUCCESS: The scheduled task "takenotes" has successfully been created.

C:\>schtasks /query /tn takenotes

Folder: \
TaskName                                 Next Run Time          Status
======================================== ====================== ===============
takenotes                                1/30/2022 11:13:00 PM  Ready

C:\>schtasks /delete /tn takenotes
WARNING: Are you sure you want to remove the task "takenotes" (Y/N)? y
SUCCESS: The scheduled task "takenotes" was successfully deleted.

C:\>schtasks /query /tn takenotes
ERROR: The system cannot find the file specified.
```

With `/create` we can define very granular time ranges or specific triggers[^2] for when a command is to launch, such as `ONSTART` or `ONLOGON`. 

To view the details of a specific tasks, you can query it by name using `/TN` and view the *XML* details with the `/XML` tag. 

```
C:\>schtasks /query /tn takenotes /xml
<?xml version="1.0" encoding="UTF-16"?>
<Task version="1.2" xmlns="http://schemas.microsoft.com/windows/2004/02/mit/task">
  <RegistrationInfo>
    <Date>2022-01-30T23:33:36</Date>
    <Author>HARTPUTER\Eddie</Author>
    <URI>\takenotes</URI>
  </RegistrationInfo>
  <Principals>
    <Principal id="Author">
      <UserId>S-1-5-21-2184681898-1587991450-2606260337-1001</UserId>
      <LogonType>InteractiveToken</LogonType>
    </Principal>
  </Principals>
  <Settings>
    <DisallowStartIfOnBatteries>true</DisallowStartIfOnBatteries>
    <StopIfGoingOnBatteries>true</StopIfGoingOnBatteries>
    <MultipleInstancesPolicy>IgnoreNew</MultipleInstancesPolicy>
    <IdleSettings>
      <Duration>PT10M</Duration>
      <WaitTimeout>PT1H</WaitTimeout>
      <StopOnIdleEnd>true</StopOnIdleEnd>
      <RestartOnIdle>false</RestartOnIdle>
    </IdleSettings>
  </Settings>
  <Triggers>
    <CalendarTrigger>
      <StartBoundary>2022-01-30T23:13:00</StartBoundary>
      <ScheduleByWeek>
        <WeeksInterval>1</WeeksInterval>
        <DaysOfWeek>
          <Sunday />
          <Monday />
          <Tuesday />
          <Wednesday />
          <Thursday />
          <Friday />
          <Saturday />
        </DaysOfWeek>
      </ScheduleByWeek>
    </CalendarTrigger>
  </Triggers>
  <Actions Context="Author">
    <Exec>
      <Command>notepad.exe</Command>
    </Exec>
  </Actions>
</Task>
```

 [^1]: #windows #fundamental 
 [^2]: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/schtasks-create
