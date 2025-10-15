## Zahard's Welcome

## Description

The base of Citadel rises before you, its great doors sealed with fractured steel and dead circuitry. Faded corporate protocols still hum in the lock, relics of the world that fell.

Those who came before tried to climb but all failed. Their echoes linger as fragments of voices, reminders of broken attempts to free humanity. Now you have chosen to take their place. You will be the one to scale the Citadel and finish what they could not.

The voices of the fallen whisper through the static: *“The path begins in the gathering place. There, candidates are chosen.”*

Here is your invitation - [https://discord.gg/FfBw8VzfRR](https://discord.gg/FfBw8VzfRR). Step into the gathering place where all climbers are briefed before the ascent.

## Writeup

Flag can be found in the rules channel of the discord server.

**Flag**: `citadel{7h3_c174d3l_b3ck0n5}`
 
# The Social Network
## Description

🗼OSINT pt1: The ascent begins. The first floor is not metal or binaries but of memory. Among the echoes, one voice lingers, of an early climber. He was among the earliest to challenge the Citadel, and though he failed, his traces remain scattered across the ruins of the old world.

It is said that the key to the next floor can be found by tracing the socials of this legendary climber. Start by checking out `citadweller` on Instagram.


## Solve

- There is a story highlight named '🗼 OSINT 1' on the [Instagram](https://instagram.com/citadweller) of `citadweller`. 
- The highlight says `citadel{17_1s_` and says to follow their [X](https://x.com/citadweller) account.
- The first tweet & bio of the X account has the second part which is `jus7_7h3_b3g1nn1ng}`

## Flag: `citadel{17_1s_jus7_7h3_b3g1nn1ng}`

## Rotting in the Deep

## Description
The floor is quiet, almost unnervingly so – like the Citadel has paused to take your measure. A soft ring of presence settles around the chamber, the kind that marks a true landing: from here, it will ask for more and, in return, grant more. Etched into its surface is a sequence of numbers, worn and faint, as if time itself is eating them away.
A whisper from the echoes guides you: 

*The message lies beneath the surface. Push it three steps forward in the cycle of life, and only then will the words emerge from the void.*


## Writeup

Flag is converted to an integer and each digit is shifted by 3. Reversing the process gets the flag.

```python
from Crypto.Util.number import *
ct = '6895840967002953721051398351211751734500850509315790892845302801984496338433523326225010635779036738800318'
flag = ''
for digit in ct:
    flag += str((int(digit)-3)%10)

print(long_to_bytes(int(flag)))
```

flag: `citadel{br0_r34lly_unr0tt3d_m3_b4ck_t0_l1f3}`

# Rotten Apple
## Description

Among the debris of this floor, you find a relic of sound: An album which turns out to be D>E>A>T>H>M>E>T>A>L by Panchiko, a long lost album. But the music is warped, as though it has undergone disc *rot*.

The path forward is hidden in the distortion. Similar to how the album was warped, the password to the next floor has been warped first by a factor of *47*, then by a factor of *13*. Untangle these changes to reveal the code and continue your ascent.

```
4:R256=Y3oRRoP0#~%Ro?A
```

## Solve

- Since the description hints at a 'rot' along with mentioning numbers 47 & 13, it's likely ROT-47 was being used and then ROT-13 and to decrypt you would have to:
  - Apply ROT-13: `4:E256=L3bEEbC0#~%Eb?N`
  - Then ROT-47: `citadel{b3tt3r_ROTt3n}`

## Flag: `citadel{b3tt3r_ROTt3n}`


