# Steady isentropic vortex

Steady isentropic vortex solution to Euler equations. Calorically perfect gas.
Widely used for simple validation in the 1990s [1].

CMT-Nek_2d_isentropic_vortex.pdf is an old document summarizing our test efforts with the
OLD, INCORRECTLY-DEALIASED version of the code. The case represented here in pvort.usr
and pvort.rea corresponds to the lower-left-hand corner of Fig. 6, p. 12. It is a periodic
2D square of 4-by-4 elements with curved edges between them.

The variable "bvort" is beta in CMT-Nek_2d_isentropic_vortex.pdf. It represents vortex strength.
Maximum Mach number, referenced somewhat clumsily to the freestream, is
exp(0.5)*beta/(2*sqrt(2)*pi)/c_sound.
It is set to 5 in useric.

There is a base flow that advects the vortex through the periodic domain. Userchk dumps
an error measurment as a function of time, with the following line appearing in the logfile
     'L2norms_sqrt ',time,err(rho),err(rho*u),err(rho*v),err(rho*w),err(rho*e)

TO DO
-stabilize the code correctly. filtering does not ever force the error to drop or plateau
 (neither did our old dealiasing effort; see Fig. 10 of CMT-Nek_2d_isentropic_vortex.pdf).
-correct the error measurement. It is not the quotient of two L2 norms, and it is not meaningful for
rho*v.

[1] Yee, Vinokur, Djomehri "Low-dissipative high-order shock-capturing methods 
using characteristic-based filters", J. Comp. Phys. 150, pp. 199-238 (1999)