# T-Clock format guide

T-Clock draws its taskbar text from a format string. Open **T-Clock Properties**, go to the format page, and type the codes below. The same list is in `T-Clock Help.rtf` next to the program.

A code in quotes is shown as written. `hh:nn "hours"` prints the time and then the word hours.

## Date

| Code | Meaning |
| --- | --- |
| `dddd` | Weekday, long. `aaaa` is the same |
| `ddd` | Weekday, short. `aaa` is the same |
| `dde` | Abbreviated weekday in English |
| `wi` | Weekday number, ISO, 1 to 7 (Monday to Sunday) |
| `wu` | Weekday number, U.S., 0 to 6 (Sunday to Saturday) |
| `dd` | Day of the month, with a leading zero |
| `d` | Day of the month |
| `mmmm` | Month name, long |
| `mmm` | Month name, short |
| `mme` | Abbreviated month name in English |
| `mm` | Month number, with a leading zero |
| `m` | Month number |
| `yyyy` | Year, four digits |
| `yy` | Year, two digits |
| `Y` | Year in the locale calendar |
| `ggg` | Era name in the locale calendar |
| `Wi` | ISO 8601 week number |
| `Wu` | U.S. week number, weeks start on Sunday |
| `Ws` | Week number, weeks start on the first Sunday |
| `Wm` | Week number, weeks start on the first Monday |
| `Ww` | Simple week number |
| `DOY` | Day of the year, 001 to 366 |
| `TZN` | Windows time-zone name on this PC. Restart T-Clock after changing it. This code does not work at the moment |

## Time

| Code | Meaning |
| --- | --- |
| `hh` | Hour, 12-hour, with a leading zero |
| `h` | Hour, 12-hour |
| `HH` | Hour, 24-hour, with a leading zero |
| `H` | Hour, 24-hour |
| `nn` | Minutes, with a leading zero |
| `n` | Minutes |
| `ss` | Seconds, with a leading zero |
| `s` | Seconds |
| `tt` | AM/PM from T-Clock's time options. `am/pm` is the same |

**Show 12:xx AM as 0:xx** changes midnight from 12 to 0. Noon stays 12.

## Other time zones

`W` is a 24-hour zone hour. `w` is a 12-hour zone hour. The offset is added to local time.

| Form | Meaning |
| --- | --- |
| `W+13` | Whole hours |
| `W-5` | Whole hours behind |
| `W+5:30` | Five hours and 30 minutes |
| `W-3:30` | Three hours and 30 minutes behind |
| `W+5.5` | Five and a half hours (30 minutes) |
| `W+5.75` | Five hours and 45 minutes |

`W+5.30` is **5.30 hours**, which is 18 minutes. For half an hour write `W+5:30` or `W+5.5`.

A bare offset prints that zone's hour. Date and time codes after it (`nn`, `ss`, `dd`, `mm`, `yyyy`, `tt`, `dddd`, and the Windows date codes) stay in that zone, so the date changes when the offset crosses midnight. The next `W` or `w` starts again from local time. Codes written **before** the offset stay on local time, which is how one format can show both clocks.

`W+5:30:"yyyy-mm-dd HH:nn"` formats only the quoted text in that zone. Use it for a second clock. India, Newfoundland, and Nepal are the usual 30-minute and 45-minute examples.

From UTC−5, `w+05` is UTC and `W+10:30:"HH:nn"` is India. `W+13:"yyyy-mm-dd HH:nn"` is China from US Eastern standard time, and the date moves ahead after 23:00. From UTC+2, `w-02` is UTC. `W+5:30:nn` prints the zone hour, then that zone's minutes.

## Other codes

| Code | Meaning |
| --- | --- |
| `\n` | Line break |
| `"..."` | Text shown as written |
| `LDATE` | Windows long date |
| `DATE` | Windows short date |
| `TIME` | Windows time |
| `@@@` | Swatch Internet beat time |
| `@@@.@` | Beat time with one decimal |
| `@@@.@@` | Beat time with two decimals |
| `JD` | Julian date |
| `OD` | Ordinal date (`YYYY-DDD`) in UTC |
| `Od` | Ordinal date in local time |
| `POSIX` | Seconds since 1970-01-01 00:00:00 UTC |

### Uptime

| Code | Meaning |
| --- | --- |
| `Sd` | Days running. Do not combine with `Sa` |
| `Sa` | Total hours running. Do not combine with `Sd` |
| `Sh` | Hours within the current day. Do not combine with `Sa` |
| `Sn` | Minutes |
| `Ss` | Seconds |
| `ST` | Short uptime, `h:mm:ss` |

Before Windows Vista, uptime uses `GetTickCount()` and wraps after 49.7 days. Vista and later do not wrap. `S__a` pads with spaces. `S___dd` keeps at least two digits.

## Command line

| Argument | Action |
| --- | --- |
| `/exit` | Exit T-Clock |
| `/prop` | Open properties |
| `/start` | Start the stopwatch |
| `/stop` | Pause the stopwatch |
| `/reset` | Reset the stopwatch to 0. This does not stop it |
| `/lap` | Record the current lap |
| `/sync` | Synchronize the clock. Windows asks for administrator approval |
| `/syncopt` | Open the time-sync options |
| `/exit-explorer` | Ask Explorer to exit |
| `/restart-explorer` | Exit Explorer, then start it again |
| `/SEH /exit` | Unload the exception handler and exit |

## PC beep tones

A `.pcb` file is plain text, one tone per line: duration in milliseconds, then frequency in hertz. A frequency of `-1` is silence. Allowed pitches are 37 to 32767. `waves/demo.pcb` is an example.

```
100, 400
100, -1
100, 500
```
