# Nested task queue and signal generator

{% embed url="https://youtu.be/ol4BzibngSg" %}

## Nested task queue

You can join multiple serial commands as one task queue:

* The token is T\_TASK\_QUEUE. ('q')
* Use 'q' to start the sequence.
* Add a sub token followed by the subcommand.
* Use ':' to add the delay time (mandatory)
* Add '>' to end the sub-command
* Example: `qk sit:1000>m 8 0 8 -30 8 0:500>` will make the robot sit and then move the shoulder joint.&#x20;

## Attach a trigonometric function to each joint to compose smooth and periodical movements

### Function

JointAngle\[index]= FunctionOf(amplitude, midpoint, freq, phase, resolution, frame)

* The token is T\_SIGNAL\_GEN. ('o')
* The command format is:`o resolution speed,jointIdx1 midpoint amplitude frequency phase,jointIdx2 midpoint amplitude frequency phase,...`
* For example: `o 1 0, 0 40 -20 4 0, 1 -30 20 4 30, 8 -70 10 4 60, 12 -10 10 4 0, 15 10 0 4 0`
* It doesn't matter if you use ',' or space ' ' to separate the numbers. However, using ',' to group can clarify one joint's parameters.

### Formula

```
for (int t = 0; t < 360; t += resolution)  
  angle = midpoint + 
         round(amp * sin(2.0 * M_PI * ((t + phase * 3 / freq) / (360.0 / freq))));
```

* The motion's iterator loops from 0 to 360.
* The resolution is how it increases to 360: t += resolution.
* The speed defines the transition speed. It will move by \[1\~125] degrees towards the target angle. 0 is the maximum speed possible.&#x20;
* frequency defines how many cycles the joint can oscillate in one loop.
* phase is defined as -120 to 120. So phase = 30 means shifting by Pi/2. 120 is one entire period.
* For example, the head’s pan/tilt angles can be bound to form the Lissajous Figure.

Pan+tilt:

`qksit:100>o 1 8, 0  0 30 4 0, 1 -30 30 4 30:100>o 1 0, 0  0 30 4 0, 1 -30 30 4 15:100>o 1 0, 0  0 30 4 0, 1 -30 30 8 30:100>o 1 8, 0 0 30 8 0, 1 -30 30 4 30:100>o 1 8, 0 0 30 4 0, 1 -30 30 16 30:100>o 1 0, 0 0 30 32 0, 1 -30 30 8 0:100>Wash face:qksit:100>i0 20 1 0 8 -70 12 0 15 10:0>o1 0, 0 40 -20 4 0, 1 -30 20 4 30, 8 -70 10 4 60, 12 -10 10 4 0, 15 10 0 4 0:100>m0 0 1 -20 2 0:0>ksit:0`

{% hint style="info" %}
For the detailed implementation, refer to the source code in OpenCatEsp32/src/OpenCat.h and reaction.h.
{% endhint %}
