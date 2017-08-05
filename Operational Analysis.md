# Operational Analysis

## Basic ABC of quantities
- A: Total number of [A]rrivals (arrivals)
- B: Total time system [B]usy (seconds)
- C: Total number of [C]ompletions (completions)
- T: Total time spent monitoring above (seconds)

## Basic derived quantities
- Arrival rate __λ__ asdasd
	- A/T (arrivals/second)
- Departure rate __X__ (exit rate)
	- C/T (completion/second)
- Server utilization __U__
	- B/T (fraction)
- Mean service time __S__ per task
	- B/C (seconds/completion)

## Utilization Law
- Utilization = Completion Rate * Service Time
- U = B/T = (C/T) * (B/C) = X*S
- Example:
	- 3 jobs per second and each job needs 0.1 second
	- Utilization of system = 3 * 0.1 = 0.3 = 30%
	- ie. how much work is done per unit of time

## Job flow balance assumption
- if Total arrivals = Total completions
- reasonable since (A-C)/C -> 0 as T -> ∞
- λ = X
- U = λS (steady state limit theorem)
	- ie. Can use arrival rate rather than departure rate
	- Have λ or X can assume the other is same

## Generalizing to network
- Let n>=1 services (servers)
- Arrival rate λ_i = A_i/T (from server i)
- Departure rate X_i = C_i/T (from server i)
- Server utilization U_i = B_i/Τ
- Main service time S_i = B_i/C_i
- Routing frequency (C_ik task goes i -> k)
	- q_ik = C_ik / C_i if i = 1...n
	- q_0k = A_0k / A_0 if i = 0

## Observations
C_i = Σ C_ik (i = 1...n)
C_0 = Σ C_k0 (completions from system)
A_0 = Σ A_0k (arrivals at system)
X_0 = Σ X_k * q_k0 (Output flow law)
Σ q_ik = 1

## Queuing at device
W_i = Σ queue lth(t)
	Area under graph (total job seconds)
Q = W/Τ
	Average queue legnth
R = W/C
	mean waiting time at i
	called response time
Q = X*R (Little's Law)
	Q = W/T = (C/T) * (W/C) = X*R

## Example
A = 7 jobs
B = 16 seconds
C = 10 jobs (3 at start)
T = 20 seconds

W = 40 job seconds
Q = W/T = 40/20 = 2 avg jobs (load = 2)
R = W/C = 40/10 = 4 seconds
U = B/T = 16/20 = 80%

## Visit ratio
- Assuming X_i = Σ X_k*q_ki
	- balanced flow
- V_i = X_i/X_O = C_i/C_O
	- mean requests per task for i
	- mean completions at i per task completion
- X_i = V_i*X_O (Forced flow law)
	- just rearranging above equation

## Visit ratio example
- Task generate on avg 5 disk requests
- disk throughput is 10 requests/second
- what is system throughput

X_O = X_i/V_i = 10 (requests/second) / 5 (requests/job)
	= 2 jobs per second
- NB using measured disk throughput
- NB All of measures irrelevant

## Interactive response time
- M users using terminals
- Mean wait time per user at terminal R
- Mean think time per user Z
- Mean thinking and waiting time (R + Z)
- (R + Z)*X_O = M = mean number of users
	- by Little's Law Q=XR
- R = (M / X_O) - Z
	- Interactive Response Time Formula
- R = (Σ Q)/X_O
	- apply Little's Law to system
- Q/X_o = V*R since
	- Q = X*R (Little's Law)
	- X = V*X_o (Forced flow law)
	- Q = V * X_o * R
- Therefore R = Σ V*R
	- General response time law
	- Total delay is sum of each delay

p20

## Example 1
params
- each task gernerates 20 disk requests => V
- disk utilization is 50% => U
- mean service time at disk 25 milliseconds => S
- 25 terminals (think time is 18 seconds) => M, Z
what is terminal response time? => R

V = 20 requests
U = 0.5 ratio
S = 0.025 seconds
M = 25 num of users
Z = 18 seconds

R = ( M / X_o ) - Z
X_o = X_d / V_d

X_o = ( U_d / S_d ) / V_d
	= ( 0.5 / 0.025 ) / 20 = 1
R = ( 25 / 1 ) - 18
	= 7 seconds

## Example 2
params
- 40 terminals
- think time 15 seconsd
- interactive response time is 5 seconds
- disk mean service time is 40 milliseconds
- each interactive task generates 10 disk I/O
- each batch job generates 5 disk I/O
- disk utilization is 90%
calculate throughput of batch and lower bound on interactive response time if batch throughput is triples

U = 0.9 ratio
V_i = 10
V_b = 5
R = 5 seconds
S = 0.04 seconds
M = 40
Z = 15 seconds

R = ( M / X_o ) - Ζ
X_o = X / V = ( U / S ) / V

Interactive throughput
	X_IO = M / ( Z + R )
		= 40 / ( 15 + 5 )
		= 2 jobs / second
Disk j throughput (interactive + batch)
	X_j = X_Ij + X_Bj = U_j / S_j
		= 0.9 / 0.04
		= 22.5 requests / second (by utilization law)

	X_Ij = V_Ij * X_Io
		= 10 * 2
		= 20 requests / second (by forced flow law)

	X_Bj = X_j - X_Ij
		= 22.5 - 20
		= 2.5 requests / second

	X_Bo = X_Bj / V_Bj
		= 2.5 / 5
		= 0.5 jobs / second

if batch throughput tripled
	X_Bo = 1.5 batch jobs / second
Disk j batch throughput
	X_Bj = V_Bj * X_Bo
		= 5 * 1.5 = 7.5 requests / second
Maximum completion rate at disk
	1/S_i = 25 requests / second (1 request = 0.04 second)
	X_Ij <= 25 - 7.5
		= 17.5 requests / second

	X_Io = X_Ij / V_Ij
		<= 17.5 / 10
		= 1.75 tasks / second

	R_I = ( M / X_Io ) - Ζ
		>= ( 40 / 1.75 ) - 15
		= 7.9 seconds
	- assuming Z,S,V,S unchanged

## Example 3

## The useful equations
- Utilization law (Very useful)
	U_i = X_i * S_i { U_i = λ_i * S_i if assume λ_i = X_i }
- Little’s law
	Q_i = X_i * R_i
- Forced flow law (Very useful)
	X_i = V_i * X_o
- General response time law
	R = Σ(i=1..n) V_i * R_i
- Interactive response time law (Very useful)
	R = ( M / X_0 ) - Z
