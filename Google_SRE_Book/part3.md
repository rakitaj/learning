# Part III. Practices

## Core learnings
SREs run services and are responsible for the health of them.

Characterize the health of a service on Maslov's SRE hierarchy of needs. The book has a pyramid illustration.

## Notes
The best way to see this is to look at the pyramid illustration in the SRE book.

The heirarchy is
1. Monitoring - is the system healthy and responding as expected? Are any problems on the horizon?
2. Incident Response - need to fix the issues raised by monitoring and otherwise. Stop the bleeding 
3. Postmortem / root cause analysis - blameless postmortems and find/fix the root cause of your problem so you aren't responding to the same incidents over and over
4. Testing + Release procedures - Don't break stuff when we release
5. Capacity Planning
6. Development
7. Product
