
2026-07-17  12:28 am

Tags: [[Customization]], [[Guide]]

---
# How to Set Up an Hourly Windows Reminder


- Search for and open **Task Scheduler** from the Windows start menu.

- In the right-hand panel, click **Create Task** (not _Create Basic Task_).

- Under the **General** tab, name your task (e.g., "Hourly Reminder").

- Go to the **Triggers** tab and click **New**:
    - Set _Begin the task:_ to **On a schedule**.
    - Set it to **Daily**.
    - At the bottom, check **Repeat task every:** and set it to **1 hour**.
    - Set _for a duration of:_ to **Indefinitely**.

- Go to the **Actions** tab and click **New**:
    - Set _Action:_ to **Start a program**.
    - In the _Program/script_ box, type: `powershell`
    - In the _Add arguments (optional)_ box, paste the following script (replace the text in quotes with your specific reminder):  
```
Add-Type -AssemblyName PresentationFramework; [System.Windows.MessageBox]::Show('Your reminder message here', 'Hourly Reminder')
```

- Click **OK** to save the task.



---
# References

Google AI Overview