C Program: Digital Clock

Aim

To write a C program to create a digital clock that displays the current time, date, and day.

Program

#include <stdio.h>
#include <time.h>
#include <unistd.h>

int main()
{
    time_t currentTime;
    struct tm *localTime;

    printf("========================================\n");
    printf("          DIGITAL CLOCK PROGRAM         \n");
    printf("========================================\n");

    while (1)
    {
        /* Get the current system time */
        time(&currentTime);

        /* Convert the time into local time */
        localTime = localtime(&currentTime);

        /* Clear the current line */
        printf("\r");

        /* Display the date */
        printf("Date : %02d-%02d-%04d    ",
               localTime->tm_mday,
               localTime->tm_mon + 1,
               localTime->tm_year + 1900);

        /* Display the time */
        printf("Time : %02d:%02d:%02d",
               localTime->tm_hour,
               localTime->tm_min,
               localTime->tm_sec);

        /* Display AM/PM */
        if (localTime->tm_hour >= 12)
            printf(" PM");
        else
            printf(" AM");

        /* Force the output to appear immediately */
        fflush(stdout);

        /* Wait for one second */
        sleep(1);
    }

    return 0;
}

Sample Output

========================================
          DIGITAL CLOCK PROGRAM
========================================

Date : 11-08-2026    Time : 18:30:01 PM
Date : 11-08-2026    Time : 18:30:02 PM
Date : 11-08-2026    Time : 18:30:03 PM
Date : 11-08-2026    Time : 18:30:04 PM

Explanation

- "time.h" is used to obtain the system date and time.
- "time()" gets the current system time.
- "localtime()" converts it into local date and time.
- "tm_hour" stores the hour.
- "tm_min" stores the minutes.
- "tm_sec" stores the seconds.
- "tm_mday" stores the date.
- "tm_mon" stores the month. Since it starts from "0", we add "1".
- "tm_year" stores the year starting from 1900, so we add "1900".
- "sleep(1)" pauses the program for one second.
- "while(1)" keeps the clock running continuously.
- "\r" moves the cursor back to the beginning of the line so the time can be updated.
