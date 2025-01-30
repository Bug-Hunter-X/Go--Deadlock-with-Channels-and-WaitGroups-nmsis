# Go Deadlock with Channels and WaitGroups

This repository demonstrates a common concurrency bug in Go involving deadlocks between goroutines using channels and wait groups. The bug occurs because the channel is closed before the receiving goroutine has a chance to process all values, leading to a deadlock.

## Bug Description
The `bug.go` file contains a program that uses a `WaitGroup` to synchronize two goroutines. One goroutine sends values to a channel, while another receives values from the channel.  However, the sending goroutine closes the channel prematurely, causing the receiving goroutine to block indefinitely, resulting in a deadlock. 

## Bug Solution
The `bugSolution.go` file provides a corrected version of the program that avoids the deadlock by ensuring that the receiving goroutine completes before the channel is closed. This is addressed by removing the premature close of the channel and relying on the range loop's inherent ability to handle channel closure to know when to exit.