------------------------------------------------------------------------

# Page 1

YAESU MUSEN CO., LTD.CAT Operation Reference Manual

------------------------------------------------------------------------

# Page 2

FT-991 CAT Operation Reference Book 1 CAT (CompuTer Aided TrAnsCeiver )
operATionOverview The CAT (Computer Aided Transceiver) System in the
FT-991A transceiver provides control of frequency, VFO, memory, and
other settings such as dual- channel memories and diversity reception
using an external personal computer. This allows multiple control
operations to be fully automated with single mouse clicks, or keystroke
operations on the computer keyboard. Using the RS-232C Cable (Refer to
figure 1) The FT-991A transceiver has a built-in level converter,
allowing direct connection from the rear-panel CAT jack to the serial
port of your computer without the need of any external boxes. When using
the RS-232C cable, set Menu item "028 GPS/232C SELECT" to "RS232C". You
will need a serial cable for connection to the RS- 232C (serial or COM
port) connector on your computer. Purchase a standard serial cable (not
the so-called "null modem" type), ensuring it has the correct gender and
number of pins (some serial COM port connectors use a 9-pin rather than
25-pin configuration). If your computer uses a custom connector, you may
have to construct the cable. In this case, refer to the technical
documentation supplied with your computer for correct data connection.
Using the USB Cable (Refer to figure 2) Note : A USB driver is required
for remote control from a computer. Download the driver from the Yaesu
website (http://www.yaesu.com). The FT-991A transceiver has a built-in
USB to Dual UART Bridge, allowing direct connection from the rear-panel
USB jack to the USB jack of your computer without the need of any
external boxes. You will need a USB cable to connect to the USB jack on
your computer. YAESU MUSEN does not produce CAT System operating
software due to the wide variety of per - sonal computers and operating
systems in use today. However, the information provided in this chapter
explains the serial data structure and opcodes used by the CAT system.
This information, along with the short programming examples, is intended
to help you start writing programs on your own. As you become more
familiar with CAT operation, you can customize programs for your
operating needs and utilize the full operating potential of this
sys-tem.COnnectiOn ①②③④⑤⑧⑨⑦⑥ Pin No. Pin Name I/O Function  N/A --- ---
 SERIAL OUT OutputOutputs the Serial Data from the transceiver to the
computer.  SERIAL IN InputInputs the Serial Data from the computer to
the transceiver.  N/A --- ---  GND --- Signal Ground  N/A --- --- 
RTS --- ---  CTS --- ---  N/A --- ---GPS/CATCOMPersonal Computer
RS-232C "Straight" CableFT-991A Figure 1 USBUSBFT-991APersonal Computer
USB Cable Figure 2

------------------------------------------------------------------------

# Page 3

FT-991 CAT Operation Reference Book 2 CAT (CompuTer Aided TrAnsCeiver )
operATioncOntrOl cOmmand A computer control command is composed of an
alpha- betical command, various parameters, and the terminator that
signals the end of the control command. Example : Set the VFO-A
frequency to 14.250000 MHz. FA 014250000 ;    Command Parameter
Terminator There are three commands for the Ft-991a as shown below: Set
command: Set a particular condition (to the Ft-991a ) Read command:
Reads an answer (from the Ft-991a ) Answer command: Transmits a
condition (from the Ft-991a ) For example, note the following case of
the FA com - mand (Set the VFO-A frequency):  To set the VFO-A
frequency to 14.250000 MHz, the following command is sent from the
computer to the transceiver: "FA014250000;" (Set command)  To read the
VFO-A frequency, the following com-mand is sent from the computer to the
transceiver: "FA;" (Read command)  When the Read command above has been
sent, the following command is returned to the computer: "FA014250000;"
(Answer command) Alphabetical Commands A command consists of 2
alphabetical characters. You may use either lower or upper case
characters. The commands available for this transceiver are listed in
the "PC Control Command Tables" on the following pages.Parameters
Parameters are used to specify information necessary to implement the
desired command. The parameters to be used for each command are pre-
determined. The number of digits assigned to each parameter is also
predetermined. Refer to the "Control Command List" and the "Control
Command Tables" to configure the appropriate parameters. When
configuring parameters, be careful not to make the following mistakes.
For example , when the correct parameter is " IS0+1000" (IF SHIFT):
IS01000 ; Not enough parameters specified (No direction (+) given for
the IF shift) IS0+100 ; Not enough digits (Only three frequency digits
given) IS0\_+\_1000 ; Unnecessary characters between parameters
IS0+10000 ; Too many digits (Five frequency digits given) Note: If a
particular parameter is not applicable to the Ft-991a, the parameter
digits should be filled using any character except the ASCII control
codes (00 to 1Fh) and the terminator ( ;). Terminator To signal the end
of a command, it is necessary to use a semicolon (; ). The digit where
this special character must appear differs depending on the command
used.

------------------------------------------------------------------------

# Page 4

FT-991 CAT Operation Reference Book 3 CAT (CompuTer Aided TrAnsCeiver )
operATionCommand Function Set Read Ans. AI AB VFO-A TO VFO-B O X X X
ACANTENNA TUNER CONTROLO O O O AG AF GAIN O O O O AI AUTO INFORMATION O
O O X AMVFO-A TO MEMORY CHANNELO X X X BA VFO-B TO VFO-A O X X X BC AUTO
NOTCH O O O O BD BAND DOWN O X X X BI BREAK-IN O O O O BP MANUAL NOTCH O
O O O BS BAND SELECT O X X X BU BAND UP O X X X BY BUSY X O O O CH
CHANNEL UP/DOWN O X X X CN CTCSS/DCS NUMBER O O O O CO CONTOUR O O O O
CS CW SPOT O O O O CT CTCSS O O O O DA DIMMER O O O X DN DOWN O X X X DT
DATE AND TIME O O O X ED ENCORDER DOWN O X X X EK ENT KEY O X X X EU
ENCORDER UP O X X X EX MENU O O O O FA FREQUENCY VFO-A O O O O FB
FREQUENCY VFO-B O O O O FS FAST STEP O O O O FT FUNCTION TX O O O O GT
AGC FUNCTION O O O O ID IDENTIFICATION X O O X IF INFORMATION X O O O IS
IF-SHIFT O O O O KM KEYER MEMORY O O O X KP KEY PITCH O O O O KR KEYER O
O O O KS KEY SPEED O O O O KY CW KEYING O X X X LK LOCK O O O O LM LOAD
MESSEGE O O O X MAMEMORY CHANNEL TO VFO-AO X X X MC MEMORY CHANNEL O O O
X MD MODE O O O O MG MIC GAIN O O O O ML MONITOR LEVEL O O O O MR MEMORY
READ X O O X MS METER SW O O O O MTMEMORY CHANNEL WRITE/TAGO O O X MW
MEMORY WRITE O X X X MX MOX SET O O O O NA NARROW O O O O NB NOISE
BLANKER O O O O NLNOISE BLANKER LEVELO O O O NR NOISE REDUCTION O O O O
OI OPPOSITE BAND NFORMATIONX O O O OSOFFSET (Repeater Shift)O O O
OCommand Function Set Read Ans. AI PA PRE-AMP (IPO) O O O O PB PLAY BACK
O O O X PC POWER CONTROL O O O O PLSPEECH PROCESSOR LEVELO O O O PR
SPEECH PROCESSOR O O O O PS POWER SWITCH O O O X QI QMB STORE O X X X QR
QMB RECALL O X X X QS QUICK SPLIT O X X X RA RF ATTENUATOR O O O O RC
CLAR CLEAR O X X X RD CLAR DOWN O X X X RG RF GAIN O O O O RI RADIO
INFORMATION X O O O RLNOISE REDUCTION LEVELO O O O RM READ METER X O O O
RS RADIO STATUS X O O X RT CLAR O O O O RU CLAR UP O X X X SC SCAN O O O
O SDSEMI BREAK-IN DELAY TIMEO O O O SH WIDTH O O O O SM S METER X O O X
SQ SQUELCH LEVEL O O O O SV SWAP VFO O X X X TS TXW O O O O TX TX SET O
O O O UL UNLOCK X O O O UP UP O X X X VD VOX DELAY TIME O O O O VG VOX
GAIN O O O O VM \[V/M\] KEY FUNCTION O X X X VX VOX O O O O XT TX CLAR O
O O O ZI ZERO IN O X X X

------------------------------------------------------------------------

# Page 5

FT-991 CAT Operation Reference Book 4 CAT (CompuTer Aided TrAnsCeiver )
operATionAB VFO-A TO VFO-B Set1 2 3 4 5 6 7 8 9 10 A B ; Read1 2 3 4 5 6
7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10 AC ANTENNA TUNER CONTROL Set1 2 3 4
5 6 7 8 9 10 P1 0: Fixed P3 0: Tuner "OFF" P2 0: Fixed 1: Tuner "ON" 2:
Tuning StartA CP1 P2 P3 ; Read1 2 3 4 5 6 7 8 9 10 A C ; Answer1 2 3 4 5
6 7 8 9 10 A CP1 P2 P3 ; AG AF GAIN Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed
P2 000 - 255 AGP1 P2 P2 P2 ; Read1 2 3 4 5 6 7 8 9 10 AGP1 ; Answer1 2 3
4 5 6 7 8 9 10 AGP1 P2 P2 P2 ; AI AUTO INFORMATION Set1 2 3 4 5 6 7 8 9
10 P1 0: Auto Information "OFF" 1: Auto Information "ON" This parameter
is set to "0" (OFF) automatically when the transceiver is turned "OFF".A
IP1 ; Read1 2 3 4 5 6 7 8 9 10 A I ; Answer1 2 3 4 5 6 7 8 9 10 A IP1 ;
AM VFO-A TO MEMORY CHANNEL Set1 2 3 4 5 6 7 8 9 10 AM ; Read1 2 3 4 5 6
7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10 BA VFO-B TO VFO-A Set1 2 3 4 5 6 7 8
9 10 B A ; Read1 2 3 4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10 BC AUTO
NOTCH Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed P2 0: Auto Notch "OFF" 1: Auto
Notch "ON"B CP1 P2 ; Read1 2 3 4 5 6 7 8 9 10 B CP1 ; Answer1 2 3 4 5 6
7 8 9 10 B CP1 P2 ; BD BAND DOWN Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed B
DP1 ; Read1 2 3 4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10

------------------------------------------------------------------------

# Page 6

FT-991 CAT Operation Reference Book 5 CAT (CompuTer Aided TrAnsCeiver )
operATionBI BREAK-IN Set1 2 3 4 5 6 7 8 9 10 P1 0: Break-in "OFF" 1:
Break-in "ON" B IP1 ; Read1 2 3 4 5 6 7 8 9 10 B I ; Answer1 2 3 4 5 6 7
8 9 10 B IP1 ; BP MANUAL NOTCH Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed P3
P2=0 P2 0: Manual NOTCH "ON/OFF" 000: "OFF" 1: Manual NOTCH LEVEL 001:
"ON" P2=1 001 - 320 (NOTCH Frequency : x 10 Hz )B PP1 P2 P3 P3 P3 ;
Read1 2 3 4 5 6 7 8 9 10 B PP1 P2 ; Answer1 2 3 4 5 6 7 8 9 10 B PP1 P2
P3 P3 P3 ; BS BAND SELECT Set1 2 3 4 5 6 7 8 9 10 P1 00: 1.8 MHz 06: 18
MHz 12: MW 01: 3.5 MHz 07: 21 MHz 13: - 02: - 08: 24.5 MHz 14: AIR 03: 7
MHz 09: 28 MHz 15: 144 MHz 04: 10 MHz 10: 50 MHz 16: 430 MHz 05: 14 MHz
11: GENB SP1 P1 ; Read1 2 3 4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10 BU
BAND UP Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed B UP1 ; Read1 2 3 4 5 6 7 8
9 10 Answer1 2 3 4 5 6 7 8 9 10 BY BUSY Set1 2 3 4 5 6 7 8 9 10 P1 0: RX
BUSY "OFF" 1: RX BUSY "ON" P2 0: Fixed Read1 2 3 4 5 6 7 8 9 10 B Y ;
Answer1 2 3 4 5 6 7 8 9 10 B YP1 P2 ; CH CHANNEL UP/DOWN Set1 2 3 4 5 6
7 8 9 10 P1 0: Memory Channel "UP" 1: Memory Channel "DOWN" C HP1 ;
Read1 2 3 4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10 CN CTCSS TONE
FREQUENCY Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed P2 0: CTCSS 1: DCS P3 P2=0
000 - 049: Tone Frequency Number (See Table 1) P2=1 000 - 103: DCS Code
Number (See Table 2)C NP1 P2 P3 P3 P3 ; Read1 2 3 4 5 6 7 8 9 10 C NP1
P2 ; Answer1 2 3 4 5 6 7 8 9 10 C NP1 P2 P3 P3 P3 ; CO CONTOUR Set1 2 3
4 5 6 7 8 9 10 P1 0: Fixed P3 P2=0 0000: CONTOUR "OFF" P2 0: CONTOUR
"ON/OFF" 0001: CONTOUR "ON" 1: CONTOUR FREQ P2=1 0010 - 3200 2: APF
"ON/OFF" (CONTOUR Frequency:10 - 3200Hz) 3: APF FREQ P2=2 0000: APF
"OFF" 0001: APF "ON" P2=3 0000 - 0050 ( APF Frequency : -250 - 250 Hz )C
OP1 P2 P3 P3 P3 P3 ; Read1 2 3 4 5 6 7 8 9 10 C OP1 P2 ; Answer1 2 3 4 5
6 7 8 9 10 C OP1 P2 P3 P3 P3 P3 ;

------------------------------------------------------------------------

# Page 7

FT-991 CAT Operation Reference Book 6 CAT (CompuTer Aided TrAnsCeiver )
operATionCS CW SPOT Set1 2 3 4 5 6 7 8 9 10 P1 0: OF F 1: ON C SP1 ;
Read1 2 3 4 5 6 7 8 9 10 C S ; Answer1 2 3 4 5 6 7 8 9 10 C SP1 ; CT
CTCSS Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed P2 0: CTCSS "OFF" 1: CTCSS
ENC/DEC 2: CTCSS ENC 3: DCS ENC/DEC 4: DCS ENCC TP1 P2 ; Read1 2 3 4 5 6
7 8 9 10 C TP1 ; Answer1 2 3 4 5 6 7 8 9 10 C TP1 P2 ; Table 1 (CTCSS
Tone Chart) 000 67.0 Hz 009 91.5 Hz 018 123.0 Hz 027 162.2 Hz 036 189.9
Hz 045 229.1 Hz 001 69.3 Hz 010 94.8 Hz 019 127.3 Hz 028 165.5 Hz 037
192.8 Hz 046 233.6 Hz 002 71.9 Hz 011 97.4 Hz 020 131.8 Hz 029 167.9 Hz
038 196.6 Hz 047 241.8 Hz 003 74.4 Hz 012 100.0 Hz 021 136.5 Hz 030
171.3 Hz 039 199.5 Hz 048 250.3 Hz 004 77.0 Hz 013 103.5 Hz 022 141.3 Hz
031 173.8 Hz 040 203.5 Hz 049 254.1 Hz 005 79.7 Hz 014 107.2 Hz 023
146.2 Hz 032 177.3 Hz 041 206.5 Hz - - 006 82.5 Hz 015 110.9 Hz 024
151.4 Hz 033 179.9 Hz 042 210.7 Hz - - 007 85.4 Hz 016 114.8 Hz 025
156.7 Hz 034 183.5 Hz 043 218.1 Hz - - 008 88.5 Hz 017 118.8 Hz 026
159.8 Hz 035 186.2 Hz 044 225.7 Hz - - Table 2 (DCS Code Chart) 000 023
015 074 030 165 045 261 060 356 075 462 090 627 001 025 016 114 031 172
046 263 061 364 076 464 091 631 002 026 017 115 032 174 047 265 062 365
077 465 092 632 003 031 018 116 033 205 048 266 063 371 078 466 093 654
004 032 019 122 034 212 049 271 064 411 079 503 094 662 005 036 020 125
035 223 050 274 065 412 080 506 095 664 006 043 021 131 036 225 051 306
066 413 081 516 096 703 007 047 022 132 037 226 052 311 067 423 082 523
097 712 008 051 023 134 038 243 053 315 068 431 083 526 098 723 009 053
024 143 039 244 054 325 069 432 084 532 099 731 010 054 025 145 040 245
055 331 070 445 085 546 100 732 011 065 026 152 041 246 056 332 071 446
086 565 101 734 012 071 027 155 042 251 057 343 072 452 087 606 102 743
013 072 028 156 043 252 058 346 073 454 088 612 103 754 014 073 029 162
044 255 059 351 074 455 089 624 - - DA DIMMER Set1 2 3 4 5 6 7 8 9 10 P1
00: Fixed P2 01 - 02: LED Indicators Brightness Level P3 00 - 15: TFT
Display Brightness LevelD AP1 P1 P2 P2 P3 P3 ; Read1 2 3 4 5 6 7 8 9 10
D A ; Answer1 2 3 4 5 6 7 8 9 10 D AP1 P1 P2 P2 P3 P3 ; DN MIC DWN Set1
2 3 4 5 6 7 8 9 10 D N ; Read1 2 3 4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8
9 10 DT DATE AND TIME Set1 2 3 4 5 6 7 \~ n-1 nP1 0: Date 1: Time (UTC)
2: Time differential (Time Zone) P2 P1=0 yyyymmdd (Year/Month/Date) P1=1
hhmmss (Hour/Minute/Second, 24 hour time system) P1=2 hhmm (Hour/Minute,
30 minute increments)D TP1 P2 P2 P2 P2 \~P2 ; Read1 2 3 4 5 6 7 8 9 10 D
TP1 ; Answer1 2 3 4 5 6 7 \~ n-1 n D TP1 P2 P2 P2 P2 \~P2 ;

------------------------------------------------------------------------

# Page 8

FT-991 CAT Operation Reference Book 7 CAT (CompuTer Aided TrAnsCeiver )
operATionED ENCORDER DOWN Set1 2 3 4 5 6 7 8 9 10 P1 0: MAIN ENCORDER 1:
SUB ENCORDER 8: MULTI ENCORDER P2 01 - 99: StepsE DP1 P2 P2 ; Read1 2 3
4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10 EK ENT KEY Set1 2 3 4 5 6 7 8
9 10 E K ; Read1 2 3 4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10 EU
ENCORDER UP Set1 2 3 4 5 6 7 8 9 10 P1 0: MAIN ENCORDER 1: SUB ENCORDER
8: MULTI ENCORDER P2 01 - 99: StepsE UP1 P2 P2 ; Read1 2 3 4 5 6 7 8 9
10 Answer1 2 3 4 5 6 7 8 9 10 EX MENU Set1 2 3 4 5 6 7 \~ n-1 nP1 :
001 - 154 (MENU Number) P2 : Parameter (See Table) E XP1 P1 P1 P2 P2
\~P2 ; Read1 2 3 4 5 6 7 8 9 10 E XP1 P1 P1 ; Answer1 2 3 4 5 6 7 \~ n-1
n E XP1 P1 P1 P2 P2 \~P2 ; P1 Function P2 Digits 001 AGC FAST DELAY 20
\~ 4000 msec (P2= 0020 \~ 4000, 20 msec/step) 4 002 AGC MID DELAY 20 \~
4000 msec (P2= 0020 \~ 4000, 20 msec/step) 4 003 AGC SLOW DELAY 20 \~
4000 msec (P2= 0020 \~ 4000, 20 msec/step) 4 004 HOME FUNCTION 0: SCOPE
1: FUNCTION 1 005 MY CALL INDICATION 0 \~ 5 sec 1 006 DISPLAY COLOR 0:
BLUE 1: GRAY 2: GREEN 3: ORANGE 4: PURPLE 5: RED 6: SKY BLUE 1 007
DIMMER LED 0: 1 1: 2 1 008 DIMMER TFT 00 \~ 15 2 009 BAR MTR PEAK HOLD
0: OFF 1: 0.5 sec 2: 1.0 sec 3: 2.0 sec 1 010 DVS RX OUT LEVEL 0 \~ 100
(P2 = 000 \~ 100) 3 011 DVS TX OUT LEVEL 0 \~ 100 (P2 = 000 \~ 100) 3
012 KEYER TYPE 0: OFF 1: BUG 2: ELEKEY-A 3: ELEKEY-B 4: ELEKEY-Y 5: ACS
1 013 KEYER DOT/DASH 0: NORNAL 1: REVERSE 1 014 CW WEIGHT 2.5 \~ 4.5 (P2
= 25 \~ 45) 2 015 BEACON INTERVAL OFF / 1 \~ 690 sec (P2 = 000 \~ 690,
000: OFF) 3 016 NUMBER STYLE 0: 1290 1: AUNO 2: AUNT 3: A2NO 4: A2NT 5:
12NO 6: 12NT 1 017 CONTEST NUMBER 0000 \~ 9999 4 018 CW MEMORY 1 0: TEXT
1: MESSAGE 1 019 CW MEMORY 2 0: TEXT 1: MESSAGE 1 020 CW MEMORY 3 0:
TEXT 1: MESSAGE 1 021 CW MEMORY 4 0: TEXT 1: MESSAGE 1 022 CW MEMORY 5
0: TEXT 1: MESSAGE 1 023 NB WIDTH 0: 1 ms 1: 3 ms 2: 10 ms 1 024 NB
REJECTION 0: 10 dB 1: 30 dB 2: 50 dB 1 025 NB LEVEL 0 \~ 10 (P2 = 00 \~
10) 2 026 BEEP LEVEL 0 \~ 100 (P2 = 000 \~ 100) 3 027 TIME ZONE UTC
--12:00 \~ +14:00 5 028 GPS/232C SELECT 0: GPS1 1: GPS2 3: RS232C 1 029
232C RATE 0: 4800 bps 1: 9600 bps 2: 19200 bps 3: 38400 bps 1 030 232C
TOT 0: 10 msec 1: 100 msec 2: 1000 msec 3: 3000 msec 1 031 CAT RATE 0:
4800 bps 1: 9600 bps 2: 19200 bps 3: 38400 bps 1 032 CAT TOT 0: 10 msec
1: 100 msec 2: 1000 msec 3: 3000 msec 1 033 CAT RTS 0: DISABLE 1: ENABLE
1 034 MEM GROUP 0: DISABLE 1: ENABLE 1 035 QUICK SPLIT FREQ --20 kHz \~
+00 (or --00) \~ +20 kHz (P2= --20 \~ +00 or --00 \~ +20) 3 036 TX TOT 0
(OFF) \~ 30 min (P2= 00 \~ 30) 2 037 MIC SCAN 0: DISABLE 1: ENABLE 1 038
MIC SCAN RESUME 0: PAUSE 1: TIME 1 039 REF FREQ ADJ --25 \~ +00 (or
--00) \~ +25 (P2= --25 \~ +00 or --00 \~ +25) 3 040 CLAR MODE SELECT 0:
RX 1: TX 2: TRX 1 041 AM LCUT FREQ 00: OFF 01: 100 Hz \~ 19: 1000 Hz (50
Hz steps) 2 042 AM LCUT SLOPE 0: 6 dB/oct 1: 18 dB/oct 1

------------------------------------------------------------------------

# Page 9

FT-991 CAT Operation Reference Book 8 CAT (CompuTer Aided TrAnsCeiver )
operATionP1 Function P2 Digits 043 AM HCUT FREQ 00: OFF 01: 700 Hz \~
67: 4000 Hz (50 Hz steps) 2 044 AM HCUT SLOPE 0: 6 dB/oct 1: 18 dB/oct 1
045 AM MIC SELECT 0: MIC 1: REAR 1 046 AM OUT LEVEL 0 \~ 100 (P2 = 000
\~ 100) 3 047 AM PTT SELECT 0: DAKY 1: RTS 2: DTR 1 048 AM PORT SELECT
0: DATA 1: USB 1 049 AM DATA GAIN 0 \~ 100 (P2 = 000 \~ 100) 3 050 CW
LCUT FREQ 00: OFF 01: 100 Hz \~ 19: 1000 Hz (50 Hz steps) 2 051 CW LCUT
SLOPE 0: 6 dB/oct 1: 18 dB/oct 1 052 CW HCUT FREQ 00: OFF 01: 700 Hz \~
67: 4000 Hz (50 Hz steps) 2 053 CW HCUT SLOPE 0: 6 dB/oct 1: 18 dB/oct 1
054 CW OUT LEVEL 0 \~ 100 (P2 = 000 \~ 100) 3 055 CW AUTO MODE 0: OFF 1:
50 MHz 2: ON 1 056 CW BK-IN TYPE 0: SEMI BREAK-IN 1: FULL BREAK-IN 1 057
CW BK-IN DELAY 30 \~ 3000 msec (P2 = 0030 \~ 3000, 10 msec/step) 4 058
CW WAVE SHAPE 0: 1 msec 1: 2 msec 2: 4 msec 3: 6 msec 1 059 CW FREQ
DISPLAY 0: DIRECT FREQ 1: PITCH OFFSET 1 060 PC KEYING 0: OFF 1: DAKY 2:
RTS 3: DTR 1 061 QSK DELAY TIME 0: 15 msec 1: 20 msec 2: 25 mesc 3: 30
msec 1 062 DATA MODE 0: PSK 1: OTHER 1 063 PSK TONE 0: 1000 Hz 1: 1500
Hz 2: 2000 Hz 1 064 OTHER DISP (SSB) --3000 Hz \~ 0 \~ +3000 Hz (P2 =
--3000 \~ --0000 or +0000 \~ +3000, 10 Hz steps) 5 065 OTHER SHIFT (SSB)
--3000 Hz \~ 0 \~ +3000 Hz (P2 = --3000 \~ --0000 or +0000 \~ +3000, 10
Hz steps) 5 066 DATA LCUT FREQ 00: OFF 01: 100 Hz \~ 19: 1000 Hz (50 Hz
steps) 2 067 DATA LCUT SLOPE 0: 6 dB/oct 1: 18 dB/oct 1 068 DATA HCUT
FREQ 00: OFF 01: 700 Hz \~ 67: 4000 Hz (50 Hz steps) 1 069 DATA HCUT
SLOPE 0: 6 dB/oct 1: 18 dB/oct 2 070 DATA IN SELECT 0: MIC 1: REAR 1 071
DATA PTT SELECT 0: DAKY 1: RTS 2: DTR 1 072 DATA PORT SELECT 1: DATA 2:
USB 1 073 DATA OUT LEVEL 0 \~ 100 (P2 = 000 \~ 100) 3 074 FM MIC SELECT
0: MIC 1: REAR 1 075 FM OUT LEVEL 0 \~ 100 (P2 = 000 \~ 100) 3 076 FM
PKT PTT SELECT 0: DAKY 1: RTS 2: DTR 1 077 FM PKT PORT SELECT 1: DATA 2:
USB 1 078 FM PKT TX GAIN 0 \~ 100 (P2 = 000 \~ 100) 3 079 FM PKT MODE 0:
1200 1: 9600 1 080 RPT SHIFT 28MHz 0 \~ 1000 kHz (P2 = 0000 \~ 1000, 10
kHz/step) 4 081 RPT SHIFT 50MHz 0 \~ 4000 kHz (P2 = 0000 \~ 4000, 10
kHz/step) 4 082 RPT SHIFT 144MHz 0 \~ 4000 kHz (P2 = 0000 \~ 4000, 10
kHz/step) 4 083 RPT SHIFT 430MHz 0 \~ 10000 kHz (P2 = 0000 \~ 10000, 10
kHz/step) 5 084 ARS 144MHz 0: OFF 1: ON 1 085 ARS 430MHz 0: OFF 1: ON 1
086 DCS POLARITY 0: Tn-Rn 1: Tn-Riv 2: Tiv-Rn 3: Tiv-Riv 1 087 RADIO
ID - - - - - - - - - - - 088 DIGITAL SQL TYPE 0: OFF 1: CODE 2: BREAK 1
089 DIGITAL SQL CODE 001 \~ 126 3 090 GM DISPLY 0: DISTANCE 1: STRENGTH
1 091 DISTANCE 0: km 1: mile 1 092 AMS TX MODE 0: AUTO 1: MANUAL 2: DN
3: VW 4: ANALOG 1 093 STANDBY BEEP 0: OFF 1: ON 1 094 RTTY LCUT FREQ 00:
OFF 01: 100 Hz \~ 19: 1000Hz (50 Hz steps) 2 095 RTTY LCUT SLOPE 0: 6
dB/oct 1: 18 dB/oct 1 096 RTTY HCUT FREQ 00: OFF 01: 700 Hz \~ 67:
4000Hz (50 Hz steps) 2 097 RTTY HCUT SLOPE 0: 6 dB/oct 1: 18 dB/oct 1
098 RTTY SHIFT PORT 0: SHIFT 1: DTR 2: RTS 1 099 RTTY POLARITY-RX 0:
NORNAL 1: REVERSE 1 100 RTTY POLARITY-TX 0: NORNAL 1: REVERSE 1 101 RTTY
OUT LEVEL 0 \~ 100 (P2 = 000 \~ 100) 3 102 RTTY SHIFT FREQ 1: 170 Hz 1:
200 Hz 2: 425 Hz 3: 850 Hz 1 103 RTTY MARK FREQ 1: 1275 Hz 2: 2125 Hz 1
104 SSB LCUT FREQ 00: OFF 01: 100 Hz \~ 19: 1000 Hz (50 Hz steps) 2 105
SSB LCUT SLOPE 0: 6 dB/oct 1: 18 dB/oct 1 106 SSB HCUT FREQ 00: OFF 01:
700 Hz \~ 67: 4000 Hz (50 Hz steps) 2 107 SSB HCUT SLOPE 0: 6 dB/oct 1:
18 dB/oct 1 108 SSB MIC SELECT 0: MIC 1: REAR 1 109 SSB OUT LEVEL 0 \~
100 (P2 = 000 \~ 100) 3 110 SSB PTT SELECT 0: DAKY 1: RTS 2: DTR 1 111
SSB PORT SELECT 0: DATA 1: USB 1 112 SSB TX BPF 0: 50 \~ 3000 1: 100 \~
2900 2: 200 \~ 2800 3: 300 \~ 2700 4: 400 \~ 2600 1 113 APF WIDTH 0:
NARROW 1: MEDIUM 2: WIDE 1 114 CONTOUR LEVEL --40 \~ 0 \~ +20 (P2 = --40
\~ --00 or +00 \~ +20) 3 115 CONTOUR WIDTH 01 \~ 11 2 116 IF NOTCH WIDTH
0: NARROW 1: WIDE 1 117 SCP DISPLAY MODE 0: SPECTRAM 1: WATER FALL 1 118
SCP SPAN FREQ 03: 50 kHz 04: 100 kHz 05: 200 kHz 06: 500 kHz 07: 1000
kHz 2 119 SPECTRUM COLOR 0: BLUE 1: GRAY 2: GREEN 3: ORANGE 4: PURPLE 5:
RED 6: SKY BLUE 1 120 WATER FALL COLOR 0: BLUE 1: GRAY 2: GREEN 3:
ORANGE 4: PURPLE 5: RED 6: SKY BLUE 7: MULTI 1 121 PRMTRC EQ1 FREQ 00 :
OFF 01: 100 02: 200 03: 300 04: 400 05: 500 06: 600 07: 700 Hz 2 122
PRMTRC EQ1 LEVEL --20 \~ 0 \~ +10 (P2 = --20 \~ --00 or +00 \~ +10) 3
123 PRMTRC EQ1 BWTH 01 \~ 10 2 124 PRMTRC EQ2 FREQ 00: OFF 01: 700 02:
800 03: 900 04: 1000 05: 1100 06: 1200 07: 1300 08: 1400 09: 1500 Hz 2

------------------------------------------------------------------------

# Page 10

FT-991 CAT Operation Reference Book 9 CAT (CompuTer Aided TrAnsCeiver )
operATionP1 Function P2 Digits 125 PRMTRC EQ2 LEVEL --20 \~ 0 \~ +10 (P2
= --20 \~ --00 or +00 \~ +10) 3 126 PRMTRC EQ2 BWTH 01 \~ 10 2 127
PRMTRC EQ3 FREQ 00 : OFF 01: 1500 02: 1600 03: 1700 04: 1800 05: 1900
06: 2000 \~ 18: 3200 Hz 2 128 PRMTRC EQ3 LEVEL --20 \~ 0 \~ +10 (P2 =
--20 \~ --00 or +00 \~ +10) 3 129 PRMTRC EQ3 BWTH 01 \~ 10 2 130
P-PRMTRC EQ1 FREQ 00 : OFF 01: 100 02: 200 03: 300 04: 400 05: 500 06:
600 07: 700 Hz 2 131 P-PRMTRC EQ1 LEVEL --20 \~ 0 \~ +10 (P2 = --20 \~
--00 or +00 \~ +10) 3 132 P-PRMTRC EQ1 BWTH 01 \~ 10 2 133 P-PRMTRC EQ2
FREQ 00: OFF 01: 700 02: 800 03: 900 04: 1000 05: 1100 06: 1200 07: 1300
08: 1400 09: 1500 Hz 2 134 P-PRMTRC EQ2 LEVEL --20 \~ 0 \~ +10 (P2 =
--20 \~ --00 or +00 \~ +10) 3 135 P-PRMTRC EQ2 BWTH 01 \~ 10 2 136
P-PRMTRC EQ3 FREQ 00 : OFF 01: 1500 02: 1600 03: 1700 04: 1800 05: 1900
06: 2000 \~ 18: 3200 Hz 2 137 P-PRMTRC EQ3 LEVEL --20 \~ 0 \~ +10 (P2 =
--20 \~ --00 or +00 \~ +10) 3 138 P-PRMTRC EQ3 BWTH 01 \~ 10 2 139 HF TX
MAX POWER 5 \~ 100 (P2 = 005 \~ 100) 3 140 50M TX MAX POWER 5 \~ 100 (P2
= 005 \~ 100) 3 141 144M TX MAX POWER 5 \~ 50 (P2 = 005 \~ 050) 3 142
430M TX MAX POWER 5 \~ 50 (P2 = 005 \~ 050) 3 143 TUNER SELECT 0: OFF 1:
INTERNAL 2: EXTERNAL 3: ATAS 4: LAMP 1 144 VOX SELECT 0: MIC 1: DATA 1
145 VOX GAIN 000 \~ 100 3 146 VOX DELAY 30 \~ 3000 msec (P2 = 0030 \~
3000, 10 msec/step) 4 147 ANTI VOX GAIN 000 \~ 100 3 148 DATA VOX GAIN
000 \~ 100 3 149 DATA VOX DELAY 30 \~ 3000 msec (P2 = 0030 \~ 3000) 4
150 ANTI DVOX GAIN 000 \~ 100 3 151 EMERGENCY FREQ TX 0: DISABLE 1:
ENABLE 1 152 PRT/WIRES FREQ 0: MANUAL 1: PRESET 1 153 PRESET FREQUENCY
00030000 \~ 47000000 8 154 SEARCH SETUP 0: HISTORY 1: ACTIVITY 1 FA
FREQUENCY VFO-A Set1 2 3 4 5 6 7 8 9 10 P1 000030000 - 470000000 (Hz)
FAP1 P1 P1 P1 P1 P1 P1 P1 11 12 13 14 15 16 17 18 19 20 P1 ; Read1 2 3 4
5 6 7 8 9 10 FA ; Answer1 2 3 4 5 6 7 8 9 10 FAP1 P1 P1 P1 P1 P1 P1 P1
11 12 13 14 15 16 17 18 19 20 P1 ; FB FREQUENCY VFO-B Set1 2 3 4 5 6 7 8
9 10 P1 000030000 - 470000000 (Hz) FBP1 P1 P1 P1 P1 P1 P1 P1 11 12 13 14
15 16 17 18 19 20 P1 ; Read1 2 3 4 5 6 7 8 9 10 FB ; Answer1 2 3 4 5 6 7
8 9 10 FBP1 P1 P1 P1 P1 P1 P1 P1 11 12 13 14 15 16 17 18 19 20 P1 ; FS
FAST STEP Set1 2 3 4 5 6 7 8 9 10 P1 0: VFO-A FAST Key "OFF" 1: VFO-A
FAST Key "ON" F SP1 ; Read1 2 3 4 5 6 7 8 9 10 F S ; Answer1 2 3 4 5 6 7
8 9 10 F SP1 ; FT FUNCTION TX Set1 2 3 4 5 6 7 8 9 10 P1 2: VFO-A Band
Transmitter: TX 3: VFO-B Band Transmitter: TX P2 0: VFO-A Band
Transmitter: TX 1: VFO-B Band Transmitter: TXF TP1 ; Read1 2 3 4 5 6 7 8
9 10 F T ; Answer1 2 3 4 5 6 7 8 9 10 F TP2 ;

------------------------------------------------------------------------

# Page 11

FT-991 CAT Operation Reference Book 10 CAT (CompuTer Aided TrAnsCeiver )
operATionGT AGC FUNCTION Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed P3 0: AGC
"OFF" P2 0: AGC "OFF" 1: AGC "FAST" 1: AGC "FAST" 2: AGC "MID" 2: AGC
"MID" 3: AGC "SLOW" 3: AGC "SLOW" 4: AGC "AUTO-FAST" 4: AGC "AUTO" 5:
AGC "AUTO-MID" 6: AGC "AUTO-SLOW"G TP1 P2 ; Read1 2 3 4 5 6 7 8 9 10 G
TP1 ; Answer1 2 3 4 5 6 7 8 9 10 G TP1 P3 ; ID IDENTIFICATION Set1 2 3 4
5 6 7 8 9 10 P1 0670: FT-991A Read1 2 3 4 5 6 7 8 9 10 ID ; Answer1 2 3
4 5 6 7 8 9 10 IDP1 P1 P1 P1 ; IF INFORMATION Set1 2 3 4 5 6 7 8 9 10 P1
001-117 (Memory Channel) P2 VFO-A Frequency (Hz) P3 Clarifier Direction
+: Plus Shift, --: Minus Shift Clarifier Offset: 0000 - 9999 (Hz) P4 0:
RX CLAR "OFF" 1: RX CLAR "ON" P5 0: TX CLAR "OFF" 1: TX CLAR "ON" P6
MODE 1: LSB 2: USB 3: CW 4: FM 5: AM 6: RTTY-LSB 7: CW-R 8: DATA-LSB 9:
RTTY-USB A: DATA-FM B: FM-N C: DATA-USB D: AM-N E: C4FM P7 0: VFO 1:
Memory 2: Memory Tune 3: Quick Memory Bank (QMB) 4: QMB-MT 5: PMS 6:
HOME P8 0: CTCSS "OFF" 1: CTCSS ENC/DEC 2: CTCSS ENC 3: DCS ENC/DEC 4:
DCS ENC P9 00: (Fixed) P10 0: Simplex 1: Plus Shift 2: Minus ShiftRead1
2 3 4 5 6 7 8 9 10 IF ; Answer1 2 3 4 5 6 7 8 9 10 IFP1 P1 P1 P2 P2 P2
P2 P2 11 12 13 14 15 16 17 18 19 20 P2 P2 P2 P2 P3 P3 P3 P3 P3 P4 21 22
23 24 25 26 27 28 29 30 P5 P6 P7 P8 P9 P9P10 ; IS IF-SHIFT Set1 2 3 4 5
6 7 8 9 10 P1 0:Fixed P2 -1000 \~ +1000 Hz (20 Hz steps) ISP1 -/+ P2 P2
P2 P2 ; Read1 2 3 4 5 6 7 8 9 10 ISP1 ; Answer1 2 3 4 5 6 7 8 9 10 ISP1
-/+ P2 P2 P2 P2 ; KM KEYER MEMORY Set1 2 3 4 5 6 7 \~ 53 nP1 1 - 5 :
Keyer Memory Channel Number P2 Message Characters (up to 50 characters)
KMP1 P2 P2 P2 P2 \~P2 ; Read1 2 3 4 5 6 7 8 9 10 KMP1 ; Answer1 2 3 4 5
6 7 \~ n-1 n KMP1 P2 P2 P2 P2 \~P2 ; KP KEY PITCH Set1 2 3 4 5 6 7 8 9
10 P1 00: 300 Hz - 75: 1050 Hz (10Hz steps) K PP1 P1 ; Read1 2 3 4 5 6 7
8 9 10 K P ; Answer1 2 3 4 5 6 7 8 9 10 K PP1 P1 ; KR KEYER Set1 2 3 4 5
6 7 8 9 10 P1 0: KEYER "OFF" 1: KEYER "ON" K RP1 ; Read1 2 3 4 5 6 7 8 9
10 K R ; Answer1 2 3 4 5 6 7 8 9 10 K RP1 ;

------------------------------------------------------------------------

# Page 12

FT-991 CAT Operation Reference Book 11 CAT (CompuTer Aided TrAnsCeiver )
operATionKS KEY SPEED Set1 2 3 4 5 6 7 8 9 10 P1 004 - 060 (WPM) K SP1
P1 P1 ; Read1 2 3 4 5 6 7 8 9 10 K S ; Answer1 2 3 4 5 6 7 8 9 10 K SP1
P1 P1 ; KY CW KEYING Set1 2 3 4 5 6 7 8 9 10 P1 1: Keyer Memory "1"
Playback 6: Message Keyer "1" Playback 2: Keyer Memory "2" Playback 7:
Message Keyer "2" Playback 3: Keyer Memory "3" Playback 8: Message Keyer
"3" Playback 4: Keyer Memory "4" Playback 9: Message Keyer "4" Playback
5: Keyer Memory "5" Playback A: Message Keyer "5" PlaybackK YP1 ; Read1
2 3 4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10 LK LOCK Set1 2 3 4 5 6 7 8
9 10 P1 0: VFO-A DIAL Lock "OFF" 1: VFO-A DIAL Lock "ON" LKP1 ; Read1 2
3 4 5 6 7 8 9 10 LK ; Answer1 2 3 4 5 6 7 8 9 10 LKP1 ; LM LOAD MESSEGE
Set1 2 3 4 5 6 7 8 9 10 P1 0: DVS P2 0: DVS (Recording Stop) 1: DVS (CH
"1" Recording Start/Stop) 2: DVS (CH "2" Recording Start/Stop) 3: DVS
(CH "3" Recording Start/Stop) 4: DVS (CH "4" Recording Start/Stop) 5:
DVS (CH "5" Recording Start/Stop)LMP1 P2 ; Read1 2 3 4 5 6 7 8 9 10 LMP1
; Answer1 2 3 4 5 6 7 8 9 10 LMP1 P2 ; MA MEMORY CHANNEL TO VFO-A Set1 2
3 4 5 6 7 8 9 10 M A ; Read1 2 3 4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9
10 MC MEMORY CHANNEL Set1 2 3 4 5 6 7 8 9 10 P1 001 - 117: Memory
Channel Number 001 - 099: Regular Memory Channel 100: P-1L 101: P-1U \~
116: P-9L 117: P-9UM CP1 P1 P1 ; Read1 2 3 4 5 6 7 8 9 10 M C ; Answer1
2 3 4 5 6 7 8 9 10 M CP1 P1 P1 ; MD OPERATING MODE Set1 2 3 4 5 6 7 8 9
10 P1 0: MAIN RX P2 MODE 1: LSB 2: USB 3: CW-U 4: FM 5: AM 6: RTTY-LSB
7: CW-L 8: DATA-LSB 9: RTTY-USB A: DATA-FM B: FM-N C: DATA-USB D: AM-N
E: C4FMM DP1 P2 ; Read1 2 3 4 5 6 7 8 9 10 M DP1 ; Answer1 2 3 4 5 6 7 8
9 10 M DP1 P2 ; MG MIC GAIN Set1 2 3 4 5 6 7 8 9 10 P1 000 - 100 M GP1
P1 P1 ; Read1 2 3 4 5 6 7 8 9 10 M G ; Answer1 2 3 4 5 6 7 8 9 10 M GP1
P1 P1 ;

------------------------------------------------------------------------

# Page 13

FT-991 CAT Operation Reference Book 12 CAT (CompuTer Aided TrAnsCeiver )
operATionML MONITOR LEVEL Set1 2 3 4 5 6 7 8 9 10 P1 0: MONI "ON/OFF" 1:
MONI Level P2 P1=0 000: MONI "OFF" 001: MONI "ON" P1=1 000 - 100M LP1 P2
P2 P2 ; Read1 2 3 4 5 6 7 8 9 10 M LP1 ; Answer1 2 3 4 5 6 7 8 9 10 M
LP1 P2 P2 P2 ; MR MEMORY CHANNEL READ Set1 2 3 4 5 6 7 8 9 10 P0/1
001-117 (Memory Channel) P2 VFO-A Frequency (Hz) P3 Clarifier Direction
+: Plus Shift, --: Minus Shift Clarifier Offset: 0000 - 9999 (Hz) P4 0:
RX CLAR "OFF" 1: RX CLAR "ON" P5 0: TX CLAR "OFF" 1: TX CLAR "ON" P6
MODE 1: LSB 2: USB 3: CW 4: FM 5: AM 6: RTTY-LSB 7: CW-R 8: DATA-LSB 9:
RTTY-USB A: DATA-FM B: FM-N C: DATA-USB D: AM-N E: C4FM P7 0: VFO 1:
Memory P8 0: CTCSS "OFF" 1: CTCSS ENC/DEC 2: CTCSS ENC 3: DCS ENC/DEC 4:
DCS ENC P9 00: (Fixed) P10 0: Simplex 1: Plus Shift 2: Minus ShiftRead1
2 3 4 5 6 7 8 9 10 M RP0 P0 P0 ; Answer1 2 3 4 5 6 7 8 9 10 M RP1 P1 P1
P2 P2 P2 P2 P2 11 12 13 14 15 16 17 18 19 20 P2 P2 P2 P2 P3 P3 P3 P3 P3
P4 21 22 23 24 25 26 27 28 29 30 P5 P6 P7 P8 P9 P9P10 ; MS METER SW Set1
2 3 4 5 6 7 8 9 10 P1 0: COMP 1: ALC 2: PO 3: SWR 4: ID 5: VDDM SP1 ;
Read1 2 3 4 5 6 7 8 9 10 M S ; Answer1 2 3 4 5 6 7 8 9 10 M SP1 ; MT
MEMORY CHANNEL WRITE/TAG Set1 2 3 4 5 6 7 8 9 10 P0/1 001-117 (Memory
Channel) P2 VFO-A Frequency (Hz) P3 Clarifier Direction +: Plus Shift,
--: Minus Shift Clarifier Offset: 0000 - 9999 (Hz)P4 0: RX CLAR "OFF" 1:
RX CLAR "ON" P5 0: TX CLAR "OFF" 1: TX CLAR "ON" P6 MODE 1: LSB 2: USB
3: CW 4: FM 5: AM 6: RTTY-LSB 7: CW-R 8: DATA-LSB 9: RTTY-USB A: DATA-FM
B: FM-N C: DATA-USB D: AM-N E: C4FM P7 Set: 0: (Fixed) / Read: 0: VFO 1:
Memory P8 0: CTCSS "OFF" 1: CTCSS ENC/DEC 2: CTCSS ENC 3: DCS ENC/DEC 4:
DCS ENC P9 00: (Fixed) P10 0: Simplex 1: Plus Shift 2: Minus Shift P11
0: (Fixed) P12 TAG Characters (up to 12 characters) (ASCII)M TP1 P1 P1
P2 P2 P2 P2 P2 11 12 13 14 15 16 17 18 19 20 P2 P2 P2 P2 P3 P3 P3 P3 P3
P4 21 22 23 24 25 26 27 28 29 30 P5 P6 P7 P8 P9 P9P10 P11 P12 P12 31 32
33 34 35 36 37 38 39 40 P12 P12 P12 P12 P12 P12 P12 P12 P12 P12 41 42 43
44 45 46 47 48 49 50 ; Read1 2 3 4 5 6 7 8 9 10 M TP0 P0 P0 ; Answer1 2
3 4 5 6 7 8 9 10 M TP1 P1 P1 P2 P2 P2 P2 P2 11 12 13 14 15 16 17 18 19
20 P2 P2 P2 P2 P3 P3 P3 P3 P3 P4 21 22 23 24 25 26 27 28 29 30 P5 P6 P7
P8 P9 P9P10 P11 P12 P12 31 32 33 34 35 36 37 38 39 40 P12 P12 P12 P12
P12 P12 P12 P12 P12 P12 41 42 43 44 45 46 47 48 49 50 ; MW MEMORY
CHANNEL WRITE Set1 2 3 4 5 6 7 8 9 10 P1 001-117 (Memory Channel) P2
Frequency (Hz) P3 Clarifier Direction +: Plus Shift, --: Minus Shift
Clarifier Offset: 0000 - 9999 (Hz)P4 0: RX CLAR "OFF" 1: RX CLAR "ON" P5
0: TX CLAR "OFF" 1: TX CLAR "ON" P6 MODE 1: LSB 2: USB 3: CW 4: FM 5: AM
6: RTTY-LSB 7: CW-R 8: DATA-LSB 9: RTTY-USB A: DATA-FM B: FM-N C:
DATA-USB D: AM-N E: C4FM P7 00: (Fixed) P8 0: CTCSS "OFF" 1: CTCSS
ENC/DEC 2: CTCSS ENC 3: DCS ENC/DEC 4: DCS ENC P9 00: (Fixed) P10 0:
Simplex 1: Plus Shift 2: Minus ShiftMWP1 P1 P1 P2 P2 P2 P2 P2 11 12 13
14 15 16 17 18 19 20 P2 P2 P2 P2 P3 P3 P3 P3 P3 P4 21 22 23 24 25 26 27
28 29 30 P5 P6 P7 P8 P9 P9P10 ; Read1 2 3 4 5 6 7 8 9 10 Answer1 2 3 4 5
6 7 8 9 10

------------------------------------------------------------------------

# Page 14

FT-991 CAT Operation Reference Book 13 CAT (CompuTer Aided TrAnsCeiver )
operATionMX MOX SET Set1 2 3 4 5 6 7 8 9 10 P1 0: MOX "OFF" 1: MOX "ON"
M XP1 ; Read1 2 3 4 5 6 7 8 9 10 M X ; Answer1 2 3 4 5 6 7 8 9 10 M XP1
; NA NARROW Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed P2 0: OFF 1: ONM AP1 P2
; Read1 2 3 4 5 6 7 8 9 10 M AP1 ; Answer1 2 3 4 5 6 7 8 9 10 M AP1 P2 ;
NB NOISE BLANKER STATUS Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed P2 0: Noise
Blanker "OFF" 1: Noise Blanker "ON"N BP1 P2 ; Read1 2 3 4 5 6 7 8 9 10 N
BP1 ; Answer1 2 3 4 5 6 7 8 9 10 N BP1 P2 ; NL NOISE BLANKER LEVEL Set1
2 3 4 5 6 7 8 9 10 P1 0: Fixed P2 000 - 010 N LP1 P2 P2 P2 ; Read1 2 3 4
5 6 7 8 9 10 N LP1 ; Answer1 2 3 4 5 6 7 8 9 10 N LP1 P2 P2 P2 ; NR
NOISE REDUCTION Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed P2 0: Noise
Reduction "OFF" 1: Noise Reduction "ON"N RP1 P2 ; Read1 2 3 4 5 6 7 8 9
10 N RP1 ; Answer1 2 3 4 5 6 7 8 9 10 N RP1 P2 ; OI OPPOSITE BAND
INFORMATION Set1 2 3 4 5 6 7 8 9 10 P1 001-117 (Memory Channel) P2 VFO-B
Frequency (Hz) P3 Clarifier Direction +: Plus Shift, --: Minus Shift
Clarifier Offset: 0000 - 9999 (Hz) P4 0: RX CLAR "OFF" 1: RX CLAR "ON"
P5 0: TX CLAR "OFF" 1: TX CLAR "ON" P6 MODE 1: LSB 2: USB 3: CW 4: FM 5:
AM 6: RTTY-LSB 7: CW-R 8: DATA-LSB 9: RTTY-USB A: DATA-FM B: FM-N C:
DATA-USB D: AM-N E: C4FM P7 0: VFO 1: Memory P8 0: CTCSS "OFF" 1: CTCSS
ENC/DEC 2: CTCSS ENC 3: DCS ENC/DEC 4: DCS ENC P9 0: (Fixed) P10 0:
Simplex 1: Plus Shift 2: Minus ShiftRead1 2 3 4 5 6 7 8 9 10 O I ;
Answer1 2 3 4 5 6 7 8 9 10 O IP1 P1 P1 P2 P2 P2 P2 P2 11 12 13 14 15 16
17 18 19 20 P2 P2 P2 P2 P3 P3 P3 P3 P3 P4 21 22 23 24 25 26 27 28 29 30
P5 P6 P7 P8 P9 P9P10 ; OS OFFSET (REPEATER SHIFT) Set1 2 3 4 5 6 7 8 9
10 P1 0: Fixed P2 0: Simplex 1: Plus Shift 2: Minus Shift \*: This
command can be activated only with an FM mode.O SP1 P2 ; Read1 2 3 4 5 6
7 8 9 10 O SP1 ; Answer1 2 3 4 5 6 7 8 9 10 O SP1 P2 ;

------------------------------------------------------------------------

# Page 15

FT-991 CAT Operation Reference Book 14 CAT (CompuTer Aided TrAnsCeiver )
operATionPA PRE-AMP (IPO) Set1 2 3 4 5 6 7 8 9 10 P1 0:Fixed P2 0: IPO
1: AMP 1 2: AMP 2P AP1 P2 ; Read1 2 3 4 5 6 7 8 9 10 P AP1 ; Answer1 2 3
4 5 6 7 8 9 10 P AP1 P2 ; PB PLAY BACK Set1 2 3 4 5 6 7 8 9 10 P1 0: DVS
P2 0: DVS (Playback Stop) 1: DVS (CH "1" Playback Start) 2: DVS (CH "2"
Playback Start) 3: DVS (CH "3" Playback Start) 4: DVS (CH "4" Playback
Start) 5: DVS (CH "5" Playback Start)PBP1 P2 ; Read1 2 3 4 5 6 7 8 9 10
PBP1 ; Answer1 2 3 4 5 6 7 8 9 10 PBP1 P2 ; PC POWER CONTROL Set1 2 3 4
5 6 7 8 9 10 P1 005 -100 PCP1 P1 P1 ; Read1 2 3 4 5 6 7 8 9 10 PC ;
Answer1 2 3 4 5 6 7 8 9 10 PCP1 P1 P1 ; PL SPEECH PROCESSOR LEVEL Set1 2
3 4 5 6 7 8 9 10 P1 000 -100 P LP1 P1 P1 ; Read1 2 3 4 5 6 7 8 9 10 P L
; Answer1 2 3 4 5 6 7 8 9 10 P LP1 P1 P1 ; PR SPEECH PROCESSOR LEVEL
Set1 2 3 4 5 6 7 8 9 10 P1 0: Speech Processor 1: Parametric Microphone
Equalizer P2 1: "OFF" 2: "ON"PRP1 P2 ; Read1 2 3 4 5 6 7 8 9 10 PRP1 ;
Answer1 2 3 4 5 6 7 8 9 10 PRP1 P2 ; PS POWER SWITCH Set1 2 3 4 5 6 7 8
9 10 P1 0: POWER "OFF" 1: POWER "ON" This command requires dummy data be
initially sent. Then after one second and be- fore two seconds the
command is sent.P SP1 ; Read1 2 3 4 5 6 7 8 9 10 P S ; Answer1 2 3 4 5 6
7 8 9 10 P SP1 ; QI QMB STORE Set1 2 3 4 5 6 7 8 9 10 Q I ; Read1 2 3 4
5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10 QR QMB RECALL Set1 2 3 4 5 6 7 8
9 10 Q R ; Read1 2 3 4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10

------------------------------------------------------------------------

# Page 16

FT-991 CAT Operation Reference Book 15 CAT (CompuTer Aided TrAnsCeiver )
operATionQS QUICK SPLIT Set1 2 3 4 5 6 7 8 9 10 Q S ; Read1 2 3 4 5 6 7
8 9 10 Answer1 2 3 4 5 6 7 8 9 10 RA RF ATTENUATOR Set1 2 3 4 5 6 7 8 9
10 P1 0: Fixed P2 0: OFF 1: ONR AP1 P2 ; Read1 2 3 4 5 6 7 8 9 10 R AP1
; Answer1 2 3 4 5 6 7 8 9 10 R AP1 P2 ; RC CLAR CLEAR Set1 2 3 4 5 6 7 8
9 10 R C ; Read1 2 3 4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10 RD CLAR
DOWN Set1 2 3 4 5 6 7 8 9 10 P1 0000 - 9999 (Hz) R DP1 P1 P1 P1 ; Read1
2 3 4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10 RG RF GAIN Set1 2 3 4 5 6
7 8 9 10 P1 0: Fixed P2 000 - 255 R GP1 P2 P2 P2 ; Read1 2 3 4 5 6 7 8 9
10 R GP1 ; Answer1 2 3 4 5 6 7 8 9 10 R GP1 P2 P2 P2 ; RI RADIO
INFORMATION Set1 2 3 4 5 6 7 8 9 10 P1 0: Hi-SWR A: TX LED P2 0: OFF 3:
REC 1: ON 4: PLAY 5: VFO-A TX 6: VFO-B TX 7: VFO-A RXRead1 2 3 4 5 6 7 8
9 10 R IP1 ; Answer1 2 3 4 5 6 7 8 9 10 R IP1 P2 ; RL NOISE REDUCTION
LEVEL Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed P2 01 - 15 R LP1 P2 P2 ; Read1
2 3 4 5 6 7 8 9 10 R LP1 ; Answer1 2 3 4 5 6 7 8 9 10 R LP1 P2 P2 ; RM
READ METER Set1 2 3 4 5 6 7 8 9 10 P1 0: Depends on the front panel
METER 4: ALC 1: S 5: PO 2: Depends on the front panel METER 6: SWR (PO /
COMP / ALC / SWR / ID / VDD) 7: ID 3: COMP 8: VDD P2 0 - 255Read1 2 3 4
5 6 7 8 9 10 RMP1 ; Answer1 2 3 4 5 6 7 8 9 10 RMP1 P2 P2 P2 ;

------------------------------------------------------------------------

# Page 17

FT-991 CAT Operation Reference Book 16 CAT (CompuTer Aided TrAnsCeiver )
operATionRS RADIO STATUS Set1 2 3 4 5 6 7 8 9 10 P1 0: NORMAL MODE 1:
MENU MODE Read1 2 3 4 5 6 7 8 9 10 R S ; Answer1 2 3 4 5 6 7 8 9 10 R
SP1 ; RT CLAR Set1 2 3 4 5 6 7 8 9 10P1 0: RX Clarifier "OFF" 1: RX
Clarifier "ON" R TP1 ; Read1 2 3 4 5 6 7 8 9 10 R T ; Answer1 2 3 4 5 6
7 8 9 10 R TP1 ; RU RX CLARIFIER PLUS OFFSET Set1 2 3 4 5 6 7 8 9 10 P1
0000 - 9999 (Hz) R UP1 P1 P1 P1 ; Read1 2 3 4 5 6 7 8 9 10 Answer1 2 3 4
5 6 7 8 9 10 SC SCAN Set1 2 3 4 5 6 7 8 9 10 P1 0: Scan "OFF" 1: Scan
"ON" (UP ward) 2: Scan "ON" (DOWN ward)S CP1 ; Read1 2 3 4 5 6 7 8 9 10
S C ; Answer1 2 3 4 5 6 7 8 9 10 S CP1 ; SD CW BREAK-IN DELAY TIME Set1
2 3 4 5 6 7 8 9 10 P1 0030 - 3000 msec S DP1 P1 P1 P1 ; Read1 2 3 4 5 6
7 8 9 10 S D ; Answer1 2 3 4 5 6 7 8 9 10 S DP1 P1 P1 P1 ; SH WIDTH Set1
2 3 4 5 6 7 8 9 10 P1 0: Fixed P2 00 (See Table) S HP1 P2 P2 ; Read1 2 3
4 5 6 7 8 9 10 S HP1 ; Answer1 2 3 4 5 6 7 8 9 10 S HP1 P2 P2 ; Command
Bandwidth P2 SSB (Narrow) SSB (Wide) CW (Narrow) CW (Wide) RTTY/PSK
(Narrow) RTTY/PSK (Wide) 00 (Default) 1500 Hz 2400 Hz 500 Hz 2400 Hz 300
Hz 500 Hz 01 200 Hz - 50 Hz - 50 Hz - 02 400 Hz - 100 Hz - 100 Hz - 03
600 Hz - 150 Hz - 150 Hz - 04 850 Hz - 200 Hz - 200 Hz - 05 1100 Hz -
250 Hz - 250 Hz - 06 1350 Hz - 300 Hz - 300 Hz - 07 1500 Hz - 350 Hz -
350 Hz - 08 1650 Hz - 400 Hz - 400 Hz - 09 1800 Hz 1800 Hz 450 Hz - 450
Hz - 10 - 1950 Hz 500 Hz 500 Hz 500 Hz 500 Hz 11 - 2100 Hz - 800 Hz -
800 Hz 12 - 2200 Hz - 1200 Hz - 1200 Hz 13 - 2300 Hz - 1400 Hz - 1400 Hz
14 - 2400 Hz - 1700 Hz - 1700 Hz 15 - 2500 Hz - 2000 Hz - 2000 Hz 16 -
2600 Hz - 2400 Hz - 2400 Hz 17 - 2700 Hz - 3000 Hz - 3000 Hz 18 - 2800
Hz - - - - 19 - 2900 Hz - - - - 20 - 3000 Hz - - - - 21 - 3200 Hz - - -
-

------------------------------------------------------------------------

# Page 18

FT-991 CAT Operation Reference Book 17 CAT (CompuTer Aided TrAnsCeiver )
operATionSM S-METER READING Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed P2 000 -
255 Read1 2 3 4 5 6 7 8 9 10 SMP1 ; Answer1 2 3 4 5 6 7 8 9 10 SMP1 P2
P2 P2 ; SQ SQUELCLH LEVEL Set1 2 3 4 5 6 7 8 9 10 P1 0: Fixed P2 000 -
100 SQP1 P2 P2 P2 ; Read1 2 3 4 5 6 7 8 9 10 SQP1 ; Answer1 2 3 4 5 6 7
8 9 10 SQP1 P2 P2 P2 ; SV SWAP VFO Set1 2 3 4 5 6 7 8 9 10 S V ; Read1 2
3 4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10 TS TXW Set1 2 3 4 5 6 7 8 9
10 P1 0: TXW "OFF" 1: TXW "ON" T SP1 ; Read1 2 3 4 5 6 7 8 9 10 T S ;
Answer1 2 3 4 5 6 7 8 9 10 T SP1 ; TX TX SET Set1 2 3 4 5 6 7 8 9 10 P1
0: RADIO TX "OFF" CAT TX "OFF" 1: RADIO TX "OFF" CAT TX "ON" 2: RADIO TX
"ON" CAT TX "OFF" (Answer)T XP1 ; Read1 2 3 4 5 6 7 8 9 10 T X ; Answer1
2 3 4 5 6 7 8 9 10 T XP1 ; UL PLL UNLOCK STATUS Set1 2 3 4 5 6 7 8 9 10
P1 0: PLL "Lock" 1: PLL "Unlock" Read1 2 3 4 5 6 7 8 9 10 U L ; Answer1
2 3 4 5 6 7 8 9 10 U LP1 ; UP UP Set1 2 3 4 5 6 7 8 9 10 U P ; Read1 2 3
4 5 6 7 8 9 10 Answer1 2 3 4 5 6 7 8 9 10 VD VOX DELAY TIME Set1 2 3 4 5
6 7 8 9 10 P1 0030 - 3000 msec (10 msec multiples) V DP1 P1 P1 P1 ;
Read1 2 3 4 5 6 7 8 9 10 V D ; Answer1 2 3 4 5 6 7 8 9 10 V DP1 P1 P1 P1
;

------------------------------------------------------------------------

# Page 19

FT-991 CAT Operation Reference Book 18 CAT (CompuTer Aided TrAnsCeiver )
operATionVG VOX GAIN Set1 2 3 4 5 6 7 8 9 10 P1 000 - 100 VGP1 P1 P1 ;
Read1 2 3 4 5 6 7 8 9 10 VG ; Answer1 2 3 4 5 6 7 8 9 10 VGP1 P1 P1 ; VM
VFO-A TO MEMORY CHANNEL Set1 2 3 4 5 6 7 8 9 10 VM ; ; Read1 2 3 4 5 6 7
8 9 10 Answer1 2 3 4 5 6 7 8 9 10 VX VOX STATUS Set1 2 3 4 5 6 7 8 9 10
P1 0: VOX "OFF" 1: VOX "ON" V XP1 ; ; Read1 2 3 4 5 6 7 8 9 10 V X ;
Answer1 2 3 4 5 6 7 8 9 10 V XP1 ; XT TX CLAR Set1 2 3 4 5 6 7 8 9 10 P1
0: TX CLAR "OFF" 1: TX CLAR "ON" X TP1 ; ; Read1 2 3 4 5 6 7 8 9 10 X T
; Answer1 2 3 4 5 6 7 8 9 10 X TP1 ; ZI ZERO IN Set1 2 3 4 5 6 7 8 9 10
(CW AUTO ZERO IN Function) Z I ; ; Read1 2 3 4 5 6 7 8 9 10 Answer1 2 3
4 5 6 7 8 9 10

------------------------------------------------------------------------

# Page 20

1612-CCopyright 2016 YAESU MUSEN CO., LTD.All rights reserved No portion
of this manual may be reproduced without the permission ofYAESU MUSEN
CO., LTD.