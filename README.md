# T-Clock Redux

A configurable clock for the Windows taskbar. It replaces the clock text with a format you write, and it can open a calendar, alarms, a stopwatch, and timers from the taskbar.

Version 2.5.0 is the current release. It continues [Stoic Joker's T-Clock 2010](http://www.stoicjoker.com/TClock/) and [White-Tiger's T-Clock Redux](https://github.com/White-Tiger/T-Clock). Kazubon wrote the original T-Clock in the 1990s.

![T-Clock on the taskbar, with its calendar open](https://cloud.githubusercontent.com/assets/1467733/4608572/71b48156-5283-11e4-960f-b0415b5b7cec.png)

## Download

**[T-Clock Redux 2.5.0](https://github.com/getprakashkc/T-Clock/releases/latest)**

The zip runs without an installer.

- On 64-bit Windows, start `Clock64.exe`.
- On 32-bit Windows, start `Clock.exe`.

Settings, the calendar, sounds, and `T-Clock Help.rtf` are in the same folder. The help file also opens from the format page inside T-Clock.

## New in 2.5.0

- **Minute time zones.** `W+5:30` and `W-3:30` are hours and minutes. `W+5.5` is five and a half hours, and `W+5.75` is five hours and 45 minutes. `W+5.30` is 5.30 hours (18 minutes), so a half hour is written `W+5:30` or `W+5.5`.
- **The date follows the zone.** `W+5:30:"yyyy-mm-dd HH:nn"` formats only the quoted text in that zone, and the date rolls after midnight there. A bare `W+5:30` prints the zone hour and keeps the following date and time codes in that zone.
- **Noon stays 12.** With "Show 12:xx AM as 0:xx" turned on, midnight is 0 and 12:00 PM stays 12.
- **The hourly chime uses local time.** In a half-hour zone it rings at the local hour, not at half past.

The [format guide](docs/format.md) lists every code.

## What it can do

- Any mix of date, time, uptime, and a second time zone in the taskbar text
- Clocks on each taskbar
- The Windows calendar and tooltip, or T-Clock's own calendar
- Alarms, a stopwatch, and timers
- Text angle, colors, and mouse actions for each button
- Portable settings in an `.ini` file next to the program
- An update check against this repository

## Run

Use it on Windows 7 or later. The 2.5.0 build was started on current Windows. Copy the `Release` folder anywhere you can write, including a USB drive. To make it portable, run `.reset_portable.cmd` once in that folder before the first start.

## Build

The supported build uses MinGW-w64. Install compilers named `i686-w64-mingw32-gcc` and `x86_64-w64-mingw32-gcc`, then from `src/~ide` run:

```
make -f linux-dll.make release_32 release_64
make -f linux-clock.make release_32 release_64
make -f linux-options.make release
make -f linux-calendar.make release
```

The programs land in `Release` and `Release/misc`. `Options.exe` and `XPCalendar.exe` are 32-bit programs, which is how this project has always shipped them.

## Support

- [Issues](https://github.com/getprakashkc/T-Clock/issues)
- [Format guide](docs/format.md)
- The older community thread is on [DonationCoder](http://donationcoder.com/forum/?board=324)

## License

The program license was left unresolved by the earlier maintainers. The pastel icons under `src/common/icons` are [CC BY-NC-SA 4.0](src/common/icons/license.txt).
