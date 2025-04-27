# Crontab Cheat Sheet

`crontab` stands for cron table — it's a configuration file that tells the system to run specific commands at specific times automatically. It's commonly used for scheduling scripts, backups, and maintenance tasks.

---

## Crontab Format

```
*     *     *     *     *     command
-     -     -     -     -
|     |     |     |     |
|     |     |     |     +----- Day of the week (0 - 7) (Sunday is both 0 and 7)
|     |     |     +------- Month (1 - 12)
|     |     +--------- Day of the month (1 - 31)
|     +----------- Hour (0 - 23)
+------------- Minute (0 - 59)
```

---

## Common Crontab Examples

| Schedule                        | Crontab Syntax         | Description                        |
|----------------------------------|-----------------------|------------------------------------|
| Every minute                    | `* * * * * command`    | Run every minute                   |
| Every 5 minutes                 | `*/5 * * * * command`  | Run every 5 minutes                |
| Every day at midnight           | `0 0 * * * command`    | Run at 00:00 every day             |
| Every Sunday at 2am             | `0 2 * * 0 command`    | Run at 2 AM on Sunday              |
| 1st of every month at 5am       | `0 5 1 * * command`    | Run at 5 AM on the first day       |
| Mon–Fri at 9am                  | `0 9 * * 1-5 command`  | Run at 9 AM Monday to Friday       |
| Reboot (special)                | `@reboot command`      | Run once when system reboots       |

---

## Useful Tips

- **Edit your crontab:**
  ```bash
  crontab -e
  ```
- **List your crontab:**
  ```bash
  crontab -l
  ```
- **Remove your crontab:**
  ```bash
  crontab -r
  ```
- **Check if cron service is running:**
  ```bash
  systemctl status cron
  ```

---

## Special Time Keywords

Instead of writing numbers, you can also use these shortcuts:

| Keyword        | Meaning                  |
|---------------|--------------------------|
| @yearly       | Once a year (Jan 1, 00:00)|
| @annually     | Same as @yearly          |
| @monthly      | Once a month (1st, 00:00) |
| @weekly       | Once a week (Sun, 00:00)  |
| @daily        | Once a day (00:00)        |
| @midnight     | Same as @daily            |
| @hourly       | Once an hour (at minute 0)|
| @reboot       | At every system reboot    |

---

## References
- https://www.runoob.com/linux/linux-comm-crontab.html
- https://www.ibm.com/docs/zh-tw/aix/7.3?topic=c-crontab-command    