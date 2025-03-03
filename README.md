# CS 261 Optimistic Replication Lab

This version of the Replication Testbed is for experimenting with a simplistic and naïve implementation of optimstic replication.

Open the .sln in Visual Studio and set the startup mode to both the Client and Server projects. Note that this code isn't very
bullet proof and it doesn't take much to break the simulation, so frequent restarts of the simulation may be required ...

# Optimistic Scenario

The server is running the simulation (it has authority) and sending updates (position and velocity) to the client. The
client is only returning back its control state (paused, not paused). The client has 3 sets of control styles for different
approaches to replication which each get updated on each frame.

## Server Controls

On the server, 'W' key controls the frequency of frame updates sent to the client. Basically, how long to 'wait' between sends.

## Simple Client

This client control updates its X and Y positions whenever it gets an update - just jumps to the new position. 
See [SimpleSyncControl.cpp](CS261_Lab/SimpleSyncControl.cpp). 

## Dead Reckoning

Using previous frame's position and velocity, predict a new position, see [DeadReckoningControl.cpp](CS261_Lab/DeadReckoningControl.cpp).

## Snapshot

Similar to dead reckoning, using the previous snapshots (two, in this case) interpolate the next position. See [SnapshotControl.cpp](CS261_Lab/SnapshotControl.cpp).

