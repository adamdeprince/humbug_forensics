Humbug forensics
================

Humbug_forensics is a little python utility for removing and faking
electrical frequency analysis foresnic data.   Wait, What's this?  Faking forensics?  

When you run a mains powered recording device, or merely sit too close
to a loaded power line with your ithingy, a small amount of A/C hum is
picked up by the recorder.  This hum comes from the alternating
current of our electrical distribution network.  And its not a perfect
tone, the actual pitch varies somewhat based on the condition of the
electrical grid.

In adversarial proceedings, like criminal cases, A/C hum is often used
to establish the time a recording was made and whether the recording
was edited.  The theory is if a recorder was stopped and restarted, the
hum on each side of the discontinuity would match a different time of
day.  This can be detected; its absense is used to "prove" that records of
confessions were not doctored.  

Except its easy to doctor.  All you need to do is apply a narrow
bandgap filter to remove the original hum and reinject new, fake, hum
data into your audio signal.  In fact, its so easy that I've created a
program that does it for you.

`humbugger --bandgap=60 --start="2013/8/1 12:00" --intensity=100 confession.wav parallely_constructed_confession.wav`

Applied above, humbugger will remove 60Hz hum data from confession.wav
and reapply hum data record from the US East Coast power grid at noon
on August 1st, 2013.


Installation
------------

humbug_forensics uses libsox, so you'll need to install that on your machine. 

Ubuntu users:

`sudo apt-get install libsox`

Macos brew users:

`brew install libsox`

Once finished 

`pip install humbug-forensics`


Cavets
------


humbugger uses data from http://dagrid.us - the hardware used to collect this
data is downright sketchy and it doesn't have the best resolution or
accuracy.  Its entirely possiable this data doesn't match the hum data
held by police departments, so a third party ENF foresnics expert may
wind up matching your audio files to a completely different time than
what you specified on the command line.

The point of this project isn't to reliably fake A/C hum data for
fradulent purposes.  The point here is to show that A/c hum data is
easy to remove and manipulate and shouldn't be considered proof of
anything.