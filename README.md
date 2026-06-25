# Windows Server RDS Learning Path 27 — Test Multiple Concurrent User Sessions

**Level:** Intermediate · **Module:** 27/70

## Goal
Validate simultaneous sessions, user isolation, application compatibility and resource consumption.

## Setup
1. Connect two or more approved users concurrently.
2. Verify each receives a distinct session ID and profile.
3. Run the same published app in both sessions.
4. Test per-user files, clipboard, printing and settings.
5. Measure CPU, memory, disk latency and network usage.
6. Record the observed user density and application conflicts.

```powershell
quser.exe
Get-RDUserSession -ConnectionBroker 'RDS01.corp.lab'
Get-Counter '\Processor(_Total)\% Processor Time',` 
 '\Memory\Available MBytes','\PhysicalDisk(_Total)\Avg. Disk sec/Transfer' `
 -SampleInterval 5 -MaxSamples 12
```

## Evidence
Store session list, isolation tests, concurrent application behavior, performance counters and capacity findings under `evidence/`.

## Troubleshooting
If users affect each other, inspect application data paths, HKLM writes, shared temp files and permissions. High latency usually requires disk and memory analysis, not only CPU checks.

## Security
Do not inspect another user's data beyond the controlled test. Use synthetic documents and accounts.

## Rollback
Log off all test sessions and remove only disposable user data.

## Next
`Windows-Server-RDS-Learning-Path-28-Monitor-and-Disconnect-RDS-Sessions`
