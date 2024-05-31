## How it works

This is a simple sequencer and driver for a 9-step 4-phase combined
power-clock PSU for adiabatic circuitry.  The rate of each phase is 1/32 the
input clock rate.  The tank capacitors are internal, 10 pF each.  There is
also an internal load capacitance of 1 pF.

It generates two sets of control signals, for phases 0 and 1.  The control
signals indicates which step of the charging circuitry should be activated. 
(Phases 2 and 3 simply invert the meaning of the steps.)

Steps 1 through 7 of phase 0 are routed to `uo[1]` through `uo[7]`.  Steps 0
and 8 of both phases 0 and 1 are routed to pins `uio[0]` through `uio[3]`.

Four "digital sync" signals are generated and routed to pins
`uio[4]` through `uio[7]`.  These mark appropriate clock cycles when data
can be latched in to or out from an adiabatic gate on phase 0 or 1.

Finally, one of the seven internal tank capacitors can be connected to
`ua[0]` by setting one of `ui[1]` through `ui[7]`.

## How to test

This project is free-running.  Simply issue a reset, then use `ui[1]`
through `ui[7]` to select which tank capacitor you wish to monitor.

## External hardware

No external hardware is necessary.
