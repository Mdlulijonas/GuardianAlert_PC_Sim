GuardianAlert PC Simulation
=============================

This is a PC simulation of GuardianAlert's embedded C logic for SIM800 modules.

Files:
- src/main.c         → program entry
- src/guardian.c     → panic alert logic (GPS + SMS)
- src/guardian.h     → header
- src/hal_mock.c     → mock HAL with fake GPS + UART output
- src/hal.h          → header for HAL interface

Build (Linux/Mac):
    gcc -o guardian_sim src/main.c src/guardian.c src/hal_mock.c


Expected Output:
    [GuardianAlert] Initializing...
    [SIMULATED UART] Sending: AT
    [GuardianAlert] Triggering panic alert...
    [SIMULATED UART] Sending: AT+CGNSINF
    [GuardianAlert] Got GPS: +CGNSINF: ...
    [SIMULATED UART] Sending: AT+CMGS="+1234567890"
    [SIMULATED UART] Sending: EMERGENCY ALERT! Help needed.
