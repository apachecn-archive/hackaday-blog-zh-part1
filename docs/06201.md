# 去抖代码——一个帖子就能解决所有问题

> 原文：<https://hackaday.com/2010/11/09/debounce-code-one-post-to-rule-them-all/>

上个月[我们要求您提交去抖代码](http://hackaday.com/2010/10/13/open-call-send-us-your-debounce-code/)。你没有让人失望，是时候分享收到的代码了。有一些发送代码的指导方针，所以如果你在这里没有看到你的，很可能没有遵守规则，抱歉。我们还尝试剔除使用延迟环路进行去抖的代码。这些往往不是处理输入的好方法，因为它们独占了处理器。

我们想在每组代码中添加向上投票/向下投票按钮，让大家对代码质量有一个共识，但是没有一个好的系统可以在一个 wordpress 页面上提供多个向上/向下投票的小部件。这导致任何人都要经历巨大的代码转储。如果你对如何更好地组织这件事有任何想法，请告诉我们:[debounce@hackaday.com](mailto:debounce@hackaday.com)。

我们不保证这段代码使用起来是安全的，甚至是有效的。在用于重要任务之前，请仔细测试。

休息之后，请加入我们的代码示例旋风。

## 奈德的去抖代码

Ned 发送了一个反跳代码包，可以监控多个按钮，对它们进行反跳，并检测按钮的保持和释放。

Main.c

```
/*****************************************************************************************
 * Project:			Button Code
 * Version:			V1.0
 * Client:			ProTechNZ
 * Date Created:	22/07/2010
 * Date Modified:	23/07/2010
 * Author:			Neil van Geffen
 * Company:			ProTech NZ

 * Micro:			ATMega128
 * Speed:			8MHz
 * Clock Source:	Internal
 *****************************************************************************************/

/************************* Defines *******************************************************/
#include &lt;io.h&gt;
#include &lt;stdlib.h&gt;
#include &lt;string.h&gt;
#include &lt;delay.h&gt;
#include &quot;NedsStandardHeader.h&quot;
#include &quot;C Files\buttons.h&quot;

#define BTN_UP			0x01
#define BTN_DOWN		0x02
#define BTN_ENTER		0x04
#define BTN_CLEAR		0x08

/************************* Structs and Enums *********************************************/

/************************* Function Prototypes *******************************************/
unsigned char TimeYet(unsigned int time);
unsigned int TimeDiff(unsigned int past, unsigned int future);
void USART0SendByte(unsigned char byteToSend);
void USART1SendByte(unsigned char byteToSend);
void USART0SendArray(unsigned char *array, unsigned char noOfBytes);
void USART0SendString(unsigned char *string);
void USART0SendStringF(flash unsigned char *string);

/************************* Global Variables***********************************************/
unsigned char tempByte;
unsigned int tempWord;

unsigned char pA, pB, pC, pD;

unsigned char releaseCounter;

volatile unsigned int isrTime;
unsigned int currentTime;
unsigned int timeButtons;
unsigned int clearPressed;

/************************* Setup Code ****************************************************/
void SetupPorts (void) {
    PORTA = 0x00;
    PORTB = 0x00;
    PORTC = 0x00;
    PORTD = 0x04;    // RXD1 (2)
    PORTE = 0x01;    // RXD0 (0)
    PORTF = 0x00;

    DDRA = 0xF0;
    DDRB = 0xFF;
    DDRC = 0xFF;
    DDRD = 0xFF;    // TXD1 (3)
    DDRE = 0x02;    // TXD0 (1)
    DDRF = 0xFF;
}

// 1mS timer
void SetupTimers (void) {
	TCCR0 = (0 &lt;&lt; FOC0) | (0 &lt;&lt; WGM00) | (0 &lt;&lt; COM01) | (0 &lt;&lt; COM00) | (1 &lt;&lt; WGM01) | (1 &lt;&lt; CS02) | (0 &lt;&lt; CS01) | (0 &lt;&lt; CS00);	// CTC 8e6/64/125 = 1KHz
	OCR0 = 124;
	TIMSK |= (1 &lt;&lt; OCIE0);
}

/************************* Main Code *****************************************************/
void main(void) {
	SetupPorts();
	SetupTimers();

	SREG.7 = 1;

	while (1)
	{
		SREG.7 = 0;											// Atomic Time Keeping
		currentTime = isrTime;
		SREG.7 = 1;

		pC &amp;= 0x07;											// keep pC to a max of 7
		pD &amp;= 0x07;											// keep pD to a max of 7
		PORTB = btnStatus.lastCount;						// output number of buttons pressed to LEDs on PortB
		PORTC = (0x80 &gt;&gt; pC);								// output a counter to PortC
		PORTD = (0x80 &gt;&gt; pD);								// output a counter to PortD

		if (TimeYet(timeButtons)) {							// Time to run this bit of code yet
			timeButtons += 5;								// Set the next time to 5mS away (can be any value really)

			UpdateButtons(currentTime);                     // Update the buttons
		}

		if (buttons.held) {									// If any button is held
			PORTF &amp;= 0x0F;									// clear the high nibble off PortF
			PORTF |= (buttons.held &lt;&lt; 4);					// and output the buttons held to PortF high nibble
			clearPressed = currentTime + 20;				// set the clearPressed time to 20ms (used to clear the LEDs after 20ms)

			switch (buttons.held) {							// do something depending on what buttons are held (can do a &quot;case BTN_UP | BTN_DOWN:&quot; if you wanted to as well)
				case BTN_UP:	pD++;		break;
				case BTN_DOWN:	pD--;		break;
				case BTN_ENTER:	pC++;		break;
				case BTN_CLEAR:	pC--;		break;
				default: pB++;
			}

			buttons.held = 0;								// Clear the buttons held flags
		}

		if (buttons.pressed) {								// if a button is pressed
			PORTF &amp;= 0xF0;									// clear the low nibble
			PORTF |= buttons.pressed;						// and set the current puttons held to the low nibble
			clearPressed = currentTime + 200;				// set the clearPressed time to 200ms to get it to clear the LEDs after 200ms

			switch (buttons.pressed) {						// do something depending on what buttons are pressed
				case BTN_UP:	pD++;		break;
				case BTN_DOWN:	pD--;		break;
				case BTN_ENTER:	pC++;		break;
				case BTN_CLEAR:	pC--;		break;
				default: pB++;
			}

			buttons.pressed = 0;							// clear the buttons pressed flags
		}

		if (buttons.released) {								// if any buttons are released
			releaseCounter++;								// increment the release counter
			PORTF = 0x00;									// clear PortF LEDs
			PORTA &amp;= 0x0F;									// clear the PortA high nibble
			PORTA |= (releaseCounter &lt;&lt; 4);					// and set what buttons were released to tht PortA LEDs

			switch (buttons.released) {						// do something on a button release
				case BTN_UP:	pD = 0;		break;
				case BTN_DOWN:	pD = 7;		break;
				case BTN_ENTER:	pC = 0;		break;
				case BTN_CLEAR:	pC = 7;		break;
				default: pB++;
			}

			buttons.released = 0;							// clear the button released flags
		}

		if (TimeYet(clearPressed)) {						// if we should clear the LEDs
			clearPressed = currentTime;						// stop the time from wrapping-over
			PORTF = 0x00;									// clear the LEDs
		}
	}
}

/************************* Functions *****************************************************/
unsigned char TimeYet(unsigned int time) {
 	if (((time - 1) - currentTime) &gt; 0xF000) {				// if the time has passed (will roll around when not serviced for 4095 counts)
    	return 1;											// the time has passed
    }
	else return 0;											// or else it has not yet passed
}

/************************* Interrupts ****************************************************/
interrupt [TIM0_COMP] void TimerZeroCompare (void) {
	isrTime++;												// Keep Time
}
```

按钮。h:

```
/************************************* START OF LIBRARY COMMENTS *******************************
* Library Name:		Neds Button Code
* Version:			V1.0
* Created:      	22/07/10
* Last Mod:			23/07/10
* CV Version:		2.04.8a
* Author:       	Neil van Geffen
* Company:      	ProTechNZ
* Purpose:      	Read 4 buttons and return button presses, helds and releases.
************************************************************************************************/

/************************************* KNOWN BUGS **********************************************
*
************************************************************************************************/

/************************************* NOTES ***************************************************
* The code will decode the button presses into presses, holds and releases.
* A press is a press AND release before a hold is registered
* A hold is a press held long enough to register as a hold.
* A hold will automatically repeat itself at an increasing rate
************************************************************************************************/

#define BUTTONS			(PINA &amp; 0x0F)		// Make the buttons the lower nibble active high (use ~ to get active low buttons to appear as active high)

#define REPEAT_MAX		250					// The start value of repeat debouncing when first pressing a button
#define REPEAT_MIN		25					// The lowest value of repeat debouncing when first holding a button
#define SPEED_SHIFT		3					// The repeat value decreases by the current repeat value &gt;&gt; by this value (aka 4 means it decreases by 1/16th every time)
#define DEBOUNCE_PRESS	25					// The debounce for a single press
#define DEBOUNCE_HOLD	600					// The debounce for a button hold

struct {
	unsigned int pressed:4;			// holds which buttons have been pressed and released
	unsigned int held:4;			// holds which buttons have been held for more than DEBOUNCE_HOLD
	unsigned int released:4;		// holds which buttons have been released after a button was held
} buttons;

#pragma used+
/***** UpdateButtons
 * Read 4 buttons (defined as BUTTONS above)
 * and save them to the buttons struct.
 * Best if called on a regulat basis like every 10mS.
 * Calling more often will give better resolution on button presses.
 ----------
 * @param - curretTime, the current time to compare the last press too to calculate debounce and press held length
 *****/
void UpdateButtons(unsigned int currentTime);
#pragma used-

#include &quot;buttons.c&quot;
```

按钮。

```
/************************************* START OF LIBRARY COMMENTS *******************************
* Library Name:		Neds Button Code
* Version:			V1.0
* Created:      	22/07/10
* Last Mod:			23/07/10
* CV Version:		2.04.8a
* Author:       	Neil van Geffen
* Company:      	ProTechNZ
* Purpose:      	Read 4 buttons and return button presses, helds and releases.
************************************************************************************************/

/************************************* KNOWN BUGS **********************************************
*
************************************************************************************************/

/************************************* NOTES ***************************************************
*
************************************************************************************************/

#define BUTTON_COUNT	((BUTTONS &amp;&amp; (BUTTONS &amp; (1 &lt;&lt; 0))) + (BUTTONS &amp;&amp; (BUTTONS &amp; (1 &lt;&lt; 1))) + (BUTTONS &amp;&amp; (BUTTONS &amp; (1 &lt;&lt; 2))) + (BUTTONS &amp;&amp; (BUTTONS &amp; (1 &lt;&lt; 3))))

#warning By compiling Neds button code, you acknowledge he is the man!

struct {
	unsigned char heldFlag:1;		// used by neds code, never change
	unsigned char decreaseFlag:1;	// used by neds code, never change

	unsigned char lastStatus:4;		// used by neds code, never change. The last valid combination of buttons pressed
	unsigned char lastCount:4;		// used by neds code, never change. The number of buttons held at one time

	unsigned int time;				// used by neds code, never change. The time the button press was changed

	unsigned int repeat;			// used by neds code, never change. The time between button held repeats
} btnStatus;

unsigned int TimeDiff(unsigned int past, unsigned int future) {
	if (((future - 1) - past) &gt; 0xF000) return 0;
	else return future - past;
}

void UpdateButtons(unsigned int currentTime) {
	if (TimeDiff(btnStatus.time, currentTime) &gt;= DEBOUNCE_HOLD) {									// If a button has been held
		if (btnStatus.decreaseFlag) {																// if the button count was lowered earlier but they have remained the same for the length of a hold time
			btnStatus.decreaseFlag = FALSE;														// clear the flag that states it was lowered
			btnStatus.lastStatus = BUTTONS;														// and set the button status to the currently pressed buttons
		}

		buttons.held = btnStatus.lastStatus;																// Set what buttons were held
		btnStatus.time += btnStatus.repeat;																// and set the time to repeat the next press
		btnStatus.repeat = MAX(REPEAT_MIN, btnStatus.repeat - MAX(1,(btnStatus.repeat &gt;&gt; SPEED_SHIFT)));		// and lower the repeat value to increase the button held repeat rate
		btnStatus.heldFlag = TRUE;																			// and set the flag that states a button was held
	}

	if (!BUTTONS) {
		if (btnStatus.heldFlag) {																	// If the buttons were previously held
			btnStatus.heldFlag = FALSE;															// Clear the flag so it doesnt set buttons pressed continously
			buttons.released = btnStatus.lastStatus;												// Set what buttons were pressed previously
		}
		else if (TimeDiff(btnStatus.time, currentTime) &gt;= DEBOUNCE_PRESS) {						// but if the buttons werent held, but pressed for long enough to pass as a debounce
			buttons.pressed = btnStatus.lastStatus;												// Set what buttons were pressed
		}

		btnStatus.lastCount = 0;																	// Clear the last count
		btnStatus.lastStatus = 0;																	// Clear the last Status
		btnStatus.time = currentTime;																// clear the last press time
	}
	else if (BUTTON_COUNT &gt; btnStatus.lastCount) {												// if the number of buttons pressed has changed
		btnStatus.lastCount = BUTTON_COUNT;														// save it for next time.
		btnStatus.lastStatus = BUTTONS;															// and save what buttons were pressed.
		btnStatus.decreaseFlag = FALSE;															// clear the flag that says the button presses just decreased.

		btnStatus.time = currentTime;																// reset the time of last button presses.
		btnStatus.repeat = REPEAT_MAX;															// and reset the time between held repeats.

	}
	else if (BUTTON_COUNT &amp;&amp; (BUTTON_COUNT &lt; btnStatus.lastCount)) {								// Or if the button count deceased but a button is still pressed
		btnStatus.lastCount = BUTTON_COUNT;														// save the count for next time
		btnStatus.decreaseFlag = TRUE;															// set the flag to say this happened

		btnStatus.time = currentTime;																// reset the time of last button presses.
		btnStatus.repeat = REPEAT_MAX;															// and reset the time between held repeats.
	}
	else if (!btnStatus.decreaseFlag &amp;&amp; (BUTTONS != btnStatus.lastStatus)) {						// If someone changed button presses but not the count
		btnStatus.lastCount = 0;																	// Force the count to change next time around so the code to set times etc isnt in 2 places.
	}                                                                   						// This is a fairly useless bit of code if the service time is less than 10mS and even if its more, it won't be all that usefull.
}
```

## S1axter 的去抖代码

这段代码是为 PIC24 芯片开发的，它反复调用一个函数来检查引脚状态。

pin_io.h:

```
//////////////////////////////////////////////////////////////////////////////////////////////////////
//
// Pin I/O control module - Header
//
// Language: Microchip C30
//
// File:     pin_io.h
// Author:   MyBitBox.com/Geeksinside.com
// Created:  08/23/09
//
//////////////////////////////////////////////////////////////////////////////////////////////////////

#ifndef __PIN_IO_H__
#define __PIN_IO_H__

void pin_io_init(void);
void pin_input_check(void);

#endif

```

pin_io.c:

```
//////////////////////////////////////////////////////////////////////////////////////////////////////
//
// Pin I/O control module
//
// Language: Microchip C30
//
// File:     pin_io.c
// Author:   MyBitBox.com/Geeksinside.com
// Created:  08/23/09
//
//////////////////////////////////////////////////////////////////////////////////////////////////////

typedef struct{
	uint16 mask;
	uint16 last_state;
	uint8 changed;
}pin_check_struct;

pin_check_struct inputA, inputB;

//====================================================================================
// Set up the pins
//====================================================================================
void pin_io_init(void)
{

	inputA.changed = FALSE;
	inputA.last_state = FALSE;
	inputA.mask = BMASK(2);       // look at PORTB2

	inputB.changed = FALSE;
	inputB.last_state = FALSE;
	inputB.mask = BMASK(4);        // look at PORTB4

	return;
}

//====================================================================================
// This is the debounce routine. When this is called it checks for consistant pin states
//====================================================================================
void pin_input_check(void)
{

	uint16 portb_snapshot = PORTB;

	// This is for the XXXXX input
	// ------------------------------------------------------
	if(inputA.changed == TRUE)
	{

		if(!((portb_snapshot ^ inputA.last_state)&amp;inputA.mask))
		{
			// If the line was changed last time, and it is the same state as last
			// time, then we need to lock it in here (If the bits are not the same then this routine
			// will be called again and the correct value will be locked in)
			if(portb_snapshot &amp; inputA.mask)
			{
				// Do this when the line goes high
				SYS_STATUS.FLAG_XXXXX_LINE = TRUE;
			}else{
				// Do this when the line goes low
				SYS_STATUS.FLAG_XXXXX_LINE = FALSE;
			}
			// Clear the changed flag
			inputA.changed = FALSE;
		}
	}
	// Mask out any changed input pins
	inputA.changed = ((inputA.last_state ^ (portb_snapshot &amp; inputA.mask))&gt;0);		// XOR with last last_state to find changed pins
	inputA.last_state = portb_snapshot &amp; inputA.mask;

	// This is for the YYYYY input
	// ------------------------------------------------------
	if(inputB.changed == TRUE)
	{

		if(!((portb_snapshot ^ inputB.last_state)&amp;inputB.mask))
		{
			// If the line was changed last time, and it is the same state as last
			// time, then we need to lock it in here (If the bits are not the same then this routine
			// will be called again and the correct value will be locked in)
			if(portb_snapshot &amp; inputB.mask)
			{
				// Do this when the line goes high
				SYS_STATUS.FLAG_YYYYY_LINE = TRUE;
			}else{
				// Do this when the line goes low
				SYS_STATUS.FLAG_YYYYY_LINE = FALSE;
			}
			// Clear the changed flag
			inputB.changed = FALSE;
		}
	}
	// Mask out any changed input pins
	inputB.changed = ((inputB.last_state ^ (portb_snapshot &amp; inputB.mask))&gt;0);		// XOR with last last_state to find changed pins
	inputB.last_state = portb_snapshot &amp; inputB.mask;

	return;
}

//end
```

## 亚伦·基思的去抖代码

这段代码是为 8051 处理器定制的。

Button_debounce_8051.c:

```
/*--------------------------------------------------------------------------
10/14/2010: Button debounce code by Aaron Keith

This code detects and debounces button presses. It is tailored for use with
8051 micro controllers.  Complied on the RIDE 51 Complier

The interrupt service routine (ISR) runs 3600 times per second.  If the
button is pressed (the pin is connected to GND) Key_Hit is incremented to the
maximum 255\.  When the button is released Key_Hit will decremented to 0.
Long_Key_Hit will increment more slowly and is used to detect the button
being help down.
--------------------------------------------------------------------------*/

#include&lt;reg51.h&gt;

#define TRUE 1
#define FALSE 0

//define pins used by buttons
at 0x97 sbit P1_7 ;
#define BUTTON P1_7   //Button on Port 1.7

//De bounce variables
unsigned char Key_Hit;
unsigned char Long_Key_Hit;

/*--------------------------------------------------------------------------
  Prototypes
--------------------------------------------------------------------------*/
void init_timers(void);

/*--------------------------------------------------------------------------
  FUNC: - Sets and starts a system timer
  PARAMS: NONE
  RETURNS: NONE
--------------------------------------------------------------------------*/
void init_timers(void)          // using a 11.0592 Mhz Clock
{
  TMOD = 0x02; //T0 mode 2 8 bit reload
  // Timer 0 is system tick

  TH0 = 0x00; // Reload = 256, giving 921600/256=3600
  TL0 = 0x00;

  ET0 = TRUE; // Enable interrupt on timer 0
  TR0 = TRUE; // Start timer 0;

  EA = TRUE;
}

/*--------------------------------------------------------------------------
  FUNC:  - Main
--------------------------------------------------------------------------*/
void main(void)
{

  init_timers(); //start the timer

  for (;;) //loop forever
    {

      if (Key_Hit == 0xff)
        {
          //Key press detected. Do something here
        }

      if (Key_Hit == 0x00)
        {
          //Key release detected. Do something here
        }

      if (Long_Key_Hit == 0xff)
        {
          //Key press and help down. Do something here
        }

    }

}

/*--------------------------------------------------------------------------
  INTERRUPT:  // The procedure runs 3600 times per second
--------------------------------------------------------------------------*/
void Timer0_interrupt(void) interrupt 1
{

  static unsigned char Div18Counter = 0;

  if (BUTTON)
    { // Button up (Pin is connected to VCC)
      if (Key_Hit != 0)  // Will never go below zero
        {
        Key_Hit--;
        }
    }
  else
    { // Button down (Pin is connected to GND)
      if (Key_Hit != 0xff)  // Will never go above 255
        {
        Key_Hit++;
        }
    }

  if (++Div18Counter &gt;= 18)   // run ever 5 mSec
    {
      Div18Counter = 0;

      if (Key_Hit == 0xff)
        {
          if (Long_Key_Hit != 0xff)
            Long_Key_Hit++;
        }
      else if (Key_Hit == 0x00)    // No delay when detecting key release.
        Long_Key_Hit = 0x00;
    }

}
```

## 托马斯·弗莱约尔斯的去抖码

该代码通过对引脚值进行移动平均来创建一个基于软件的低通滤波器。

```
// Hi, to prevent contact bounce, my solution is to create software low pass filter by using a moving average...(no delay solution) see the jpg to see what's happen
// INPUT is the button input pin(0if not pressed, 1 if pressed)

main(void)
{
    unsigned char button = 0;
    while(1)
    {
         // your code here...

         button=(button * 9+INPUT * 10)/10; // do a moving average of the digital input... result button between 0 and 10

         if (button &gt; 5)
         {
                //the button is ON
         }
         else
         {
                //the button is OFF
         }

    }
}
```

## 甘尼什·克里希纳的去抖动代码

可以缩放到任意数量的按钮，采样率是可配置的，这旨在使用尽可能少的 RAM

dbounce.c:

```
#include &lt;htc.h&gt;

/* Scalable software debounce for buttons
 *
 * This is quick implementation of software debounce with as little RAM as possible.
 * stress is given to scalability of number of buttons
 * and scalability of number of samples per debounce cycle.
 *
 * While this file is written for PIC Microcontroller and Hi-tech compiler,
 * the debounce function itself is just C, and not hardware dependant.
 *
 * Use the functions at your own risk
 * Author: ganesh.ksm@gmail.com
 *
 * Assume BSD like license.
 * Acknowledge with an email if it works for you.
 *
*/

/*Number of buttons in the system*/
#define MAX_BUTTONS 4

/* MAJORITY_VOTE Number of samples for which the button must remain in pressed state
 * to consider that the button is pressed.
 * */
#define MAJORITY_VOTE 5

/* STABILITY_BITS is the number of final samples (last few samples at the end of debounce)
 * after which we consider the input stable
 * */
#define STABILITY_BITS 2

/* Convert Stability bits to a bit mask, i.e STABILITY_MASK has STABILITY_BITS bits set in its LSB
 * */
#define STABILITY_MASK ((1&lt;&lt;STABILITY_BITS) - 1)

/*This variable contains the debounced status of all buttons
   at any point of time
   */
volatile unsigned int debounced_buttons;

/* Reads port pins and returns 1 if button is active (assumed active low)
 * returns 0 if inactive. Microchip PIC18 specific.
 * */
unsigned char Read_Portbit(int button)
{
	switch(button)
	{
		case 0: return !RA0;
		case 1: return !RA1;
		case 2: return !RA2;
		case 3: return !RA3;
	}
}

/* Function: button_is_pressed()
 * Argument: Takes the button number as argument, an index into the array of buttons.
 * Returns:  non zero if the button of interest is pressed for majority time of polling
 *           returns zero if not pressed, debouncing not complete,
 *           button bouced back to unpressed state
 *
 * Calling rate: This function will return positive only after MAJORITY_VOTE is achieved
 *  times with same button argument for debounce of one button.
 * 		 where X is the number of samples per debounce,
 *
 * Depends on: Read_Portbit(button) which returns 1 if the pin of button of interest is active and 0 if not.
 */
char button_is_pressed( unsigned char button)
{
	unsigned int bit_count=0, temp;

	/* button_bits[] is an array to hold the previous states of the port pin value
	 * Each element holds the previous samples of teh button read.
	 * We need as many elements as there are buttons.
	 * Make this an integer array if more than 8 samples are needed for debounce determination.
	 * if less samples are needed adjust the MAJORITY_VOTE and STABILITY_BITS to a smaller number
	 * */

volatile static unsigned char button_bits[MAX_BUTTONS];

	/* Shift the latest read button status into the que
	 * we should have the latest sample in LSB and older samples
	 * higher up.*/

	button_bits[button]=button_bits[button]&lt;&lt;1 | (Read_Portbit(button) &amp; 0x01);
	temp = button_bits[button];

	/*Check if the input is stable in the last STABILITY_BITS samples*/
	if ((temp &amp; STABILITY_MASK) == STABILITY_MASK)
	{
		/* Count the number of bits set in temp, we need more than the majority
		 * straight out of the book of K&amp;R, check it :-)*/
		while(temp = temp&amp;(temp-1))
			bit_count++;
		bit_count++; // we are off by one

		/*Check if the required number of samples were favourable */
		if (bit_count&gt;=MAJORITY_VOTE)
		{
			button_bits[button] = 0;
			return 1;
		}
		else
			return 0;
	}
	else
	{
		return 0;
	}
}

/* Call at a rate about 8 times higher than the rate at which input detection is required
 * actual frequency depends on the number of samples required per debounce.
  */

void Service_user_Input(void)
{
	int i;
	for (i=0;i&lt;MAX_BUTTONS;i++)
	{
		if (button_is_pressed(i))
			debounced_buttons = debounced_buttons | 0x01&lt;&lt;i;
	}
}

void main (void)
{
	/*PIC18 specific intialization of timer interrupt*/
	GIE=1;
	PEIE=1;
	TMR0IE=1;

	T0CON= 0X48;    //16 bit timer without Prescaler for interrupts
	TMR0L=0xFA;
	TMR0H=0xFF;
	TMR0ON=1;
	TRISA = 0xFF; // PORTA is input.
	/*Application code starts here*/
	while(1)
	{
		/*Do something usefull with debounced_buttons*/
	}

}

void interrupt User_Input()
{
	TMR0L=0x00; /*Not really needed, but lets be explicit*/
	TMR0H=0x00;
	TMR0ON=1;

	Service_user_Input(); /*you may choose to call this in an timed function in the main thread too*/
}
```

## 肯尼斯·库恩的去抖代码

[Chad]使用[[Kenneth Kuhn 的]去抖代码](http://www.kennethkuhn.com/electronics/debounce.c)的修改版本已经有一段时间了。小，快，注释好，它使用积分算法。

去抖 c:

```
/******************************************************************************

debounce.c
written by Kenneth A. Kuhn
version 1.00

This is an algorithm that debounces or removes random or spurious
transistions of a digital signal read as an input by a computer.  This is
particularly applicable when the input is from a mechanical contact.  An

integrator is used to perform a time hysterisis so that the signal must
persistantly be in a logical state (0 or 1) in order for the output to change
to that state.  Random transitions of the input will not affect the output

except in the rare case where statistical clustering is longer than the
specified integration time.

The following example illustrates how this algorithm works.  The sequence
labeled, real signal, represents the real intended signal with no noise.  The

sequence labeled, corrupted, has significant random transitions added to the
real signal.  The sequence labled, integrator, represents the algorithm
integrator which is constrained to be between 0 and 3\.  The sequence labeled,

output, only makes a transition when the integrator reaches either 0 or 3.
Note that the output signal lags the input signal by the integration time but
is free of spurious transitions.

real signal 0000111111110000000111111100000000011111111110000000000111111100000

corrupted   0100111011011001000011011010001001011100101111000100010111011100010
integrator  0100123233233212100012123232101001012321212333210100010123233321010
output      0000001111111111100000001111100000000111111111110000000001111111000

I have been using this algorithm for years and I show it here as a code
fragment in C.  The algorithm has been around for many years but does not seem
to be widely known.  Once in a rare while it is published in a tech note.  It

is notable that the algorithm uses integration as opposed to edge logic
(differentiation).  It is the integration that makes this algorithm so robust
in the presence of noise.
******************************************************************************/

/* The following parameters tune the algorithm to fit the particular
application.  The example numbers are for a case where a computer samples a
mechanical contact 10 times a second and a half-second integration time is

used to remove bounce.  Note: DEBOUNCE_TIME is in seconds and SAMPLE_FREQUENCY
is in Hertz */

#define DEBOUNCE_TIME		0.3
#define SAMPLE_FREQUENCY	10
#define MAXIMUM			(DEBOUNCE_TIME * SAMPLE_FREQUENCY)

/* These are the variables used */
unsigned int input;       /* 0 or 1 depending on the input signal */
unsigned int integrator;  /* Will range from 0 to the specified MAXIMUM */
unsigned int output;      /* Cleaned-up version of the input signal */

/* Step 1: Update the integrator based on the input signal.  Note that the
integrator follows the input, decreasing or increasing towards the limits as
determined by the input state (0 or 1). */

  if (input == 0)

    {
    if (integrator &gt; 0)
      integrator--;
    }
  else if (integrator &lt; MAXIMUM)
    integrator++;

/* Step 2: Update the output state based on the integrator.  Note that the
output will only change states if the integrator has reached a limit, either

0 or MAXIMUM. */

  if (integrator == 0)
    output = 0;
  else if (integrator &gt;= MAXIMUM)
    {
    output = 1;
    integrator = MAXIMUM;  /* defensive code if integrator got corrupted */
    }

/********************************************************* End of debounce.c */
```

## Ubi de Feo 的去抖码

Arduino 草图从一个数组中去抖引脚。

```
#define ARRAY_SIZE 8
// array of pins to be debounced
short pinsToDebounce[]={
  2,3,4,5,6,7,8,9
};
// array of pin state
int swStates[]={
  0,0,0,0,0,0,0,0};
// array of previous pin state
int swPrevStates[]={
  0,0,0,0,0,0,0,0};
// array to store the actual state during debounce
int swDebouncedStates[]={
  0,0,0,0,0,0,0,0};
// array to store the previous state during debounce
int swPrevDebounceStates[]={0,0,0,0,0,0,0,0};
// time to debounce
int debounceDelay=100;
// array of previous times the pin has been checked
long prevTimes[]={
  0,0,0,0,0,0,0,0};

void setup(){
  Serial.begin(9600);

 initSwitches();
}
void loop(){
 readSwitches();
}

void initSwitches(){
  for(int i=0;i&lt;ARRAY_SIZE;i++){
    pinMode(pinsToDebounce[i],INPUT);
  }
}
void readSwitches(){

  // Serial.print(&quot;active switch set &quot;);
  // Serial.println((int)activeSwitchSet);

  for(short sw=0;sw&lt;ARRAY_SIZE;sw++){
    volatile int pin=pinsToDebounce[sw];
    volatile int mpPin=pin;
    volatile int pinPosition=sw;

    swStates[pinPosition]=digitalRead(pin);
  }

  debouncePins();
   checkStateChange();
}
void debouncePins(){

  volatile long _millis=millis();

  for(short sw=0;sw&lt;ARRAY_SIZE;sw++){
    if(swStates[sw]!=swPrevStates[sw]){
      prevTimes[sw]=_millis;
    }
    if(_millis-prevTimes[sw]&gt;debounceDelay){
      prevTimes[sw]=_millis;
      swDebouncedStates[sw]=swStates[sw];
      /*
      Serial.print(&quot;button &quot;);
       Serial.print(sw);
       Serial.print(&quot; is &quot;);
       Serial.println(swDebouncedStates[sw]);
       */
    }
    swPrevStates[sw]=swStates[sw];
  }

}

void checkStateChange(){
  for(short sw=0;sw&lt;5;sw++){
    if(swPrevDebounceStates[sw]!=swDebouncedStates[sw]){
      /*
      Serial.println(&quot;&quot;);
      Serial.print(&quot;button &quot;);
      Serial.print(sw);
      Serial.print(&quot; &quot;);
      Serial.println(swDebouncedStates[sw]);
      */
      if(swDebouncedStates[sw]==1){
        pinActive(sw);
      }
      if(swDebouncedStates[sw]==0){
        pinInactive(sw);
      }
    }
    swPrevDebounceStates[sw]=swDebouncedStates[sw];
  }
}

void printDebStates(){
  Serial.println(&quot;%%%%%%%%%%%%%%%%%%%%%%%%&quot;);
  for(int i=0;i&lt;ARRAY_SIZE;i++){
    Serial.print(swDebouncedStates[i]);
    Serial.print('*');

  }

  Serial.println(&quot;&quot;);
}
void pinActive(int _id){

  Serial.print(&quot;active pin &quot;);
  Serial.println(pinsToDebounce[_id]);
}
void pinInactive(int _id){
   Serial.print(&quot;inactive pin &quot;);
 Serial.println(pinsToDebounce[_id]);
}
```

## 克里斯托夫·贡梅尔的《债务法典》

用 STM32 ARM 处理器去抖和扫描键盘矩阵。

```
/*
  keyboard.c
  Used on an STM32F103 in a wireless remote control
  (C) 2010 Christoph Gommel &lt;chg@contronix.de&gt;
  Contronix GmbH, Nizzastr. 6, 01445 Radebeul, Germany
  Tags: matrix, keyboard, stm32, stm32f103, debounce, hackaday
 */
#include &quot;stm32f10x.h&quot;
#include &quot;keyboard.h&quot;
#include &quot;fifo.h&quot;

#define KEYBOARD_GPIO (GPIOA)

// Cols and rows are intentionally placed in the right order enabling the bit shifting trick used.

#define COL1 (GPIO_Pin_1)
#define COL2 (GPIO_Pin_2)
#define COL3 (GPIO_Pin_3)
#define COLS (COL1|COL2|COL3)

#define ROW1 (GPIO_Pin_4)
#define ROW2 (GPIO_Pin_5)
#define ROW3 (GPIO_Pin_6)
#define ROW4 (GPIO_Pin_7)
#define ROW5 (GPIO_Pin_8)
#define ROWS (ROW1|ROW2|ROW3|ROW4|ROW5)
//#define ROWS_B (ROW5)

#define ColNum (3)
#define RowNum (5)

#define ColStart (1)
#define RowStart (4)

//Very useful macro to increment and modulo in one instruction
#define incmod(n,m); n=((n+1)%m);

// Yes, we have a shift key too
#define SHIFT (GPIO_Pin_0)

GPIO_InitTypeDef GPIO_InitStructure;

#define KeyBufferSize (20)

//volatile unsigned char keypad_queue_buffer[KeyBufferSize];

static char keypad_queue_buffer[KeyBufferSize];
fifo_t keyfifo;

void keyboard_init(void)
{
  //Initialize a self made fifo system
  fifo_init(&amp;keyfifo, keypad_queue_buffer, KeyBufferSize);

  //Give clock to the GPIO
  RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOA, ENABLE);

  //Initialize the rows as push-pull-output
  GPIO_InitStructure.GPIO_Pin = ROWS;
  GPIO_InitStructure.GPIO_Speed = GPIO_Speed_2MHz;
  GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
  GPIO_Init(KEYBOARD_GPIO, &amp;GPIO_InitStructure);

  //The cols ar input with pull-up
  GPIO_InitStructure.GPIO_Pin = COLS | SHIFT;
  GPIO_InitStructure.GPIO_Speed = GPIO_Speed_2MHz;
  GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IPU;
  GPIO_Init(KEYBOARD_GPIO, &amp;GPIO_InitStructure);

  GPIO_SetBits(KEYBOARD_GPIO, ROWS);

}

volatile unsigned int CurrentRow = 0;
volatile unsigned int lastScan = 0;
volatile unsigned int thisScan = 0;
volatile unsigned int debounceCnt;
volatile unsigned int numberOfKeys;
volatile unsigned int thisScancode;
volatile unsigned int lastScancode;

//Adapt this to you wishes
#define debounceMax (10)

//The following piece of code will be called every 10 ms from a systick interrupt
void keyboard_scan(void)
{
  unsigned int scan;
  scan = ((~GPIO_ReadInputData(KEYBOARD_GPIO)) &amp; COLS) &gt;&gt; ColStart;

  //this is the really interesting core of my matrix scanning algorithm.
  //each key of the matrix is represented in one bit of a 16 bit unsigned short ;)
  thisScan = (thisScan | (scan &lt;&lt; (ColNum * RowNum))) &gt;&gt; ColNum;
  //Release Current Row
  GPIO_SetBits(KEYBOARD_GPIO, 1 &lt;&lt; (CurrentRow + RowStart));

  incmod(CurrentRow,RowNum);
  //prepare next Row

  GPIO_ResetBits(KEYBOARD_GPIO, 1 &lt;&lt; (CurrentRow + RowStart));

  if (0 == CurrentRow)
  {
    //Something changed, let's reset the debounce counter
    if (thisScan != lastScan)
    {
      debounceCnt = 0;
    }
    //...or increase if nothing changed
    else if (debounceCnt &lt; debounceMax)
    {
      debounceCnt++;
    }
    //... if the threshold is reached
    if (debounceCnt == debounceMax)
    {
      numberOfKeys = 0;
      int i;
      //count the number of keys pressed and mark the position of the set bit in &quot;thisScancode&quot;
      for (i = 0; i &lt; (ColNum * RowNum); i++)
        if (thisScan &amp; (1 &lt;&lt; i))
        {
          numberOfKeys++;
          thisScancode = i + 1;
        }
      //ignore multiple key presses...
      if (1 != numberOfKeys)
        thisScancode = 0;
      else
      {
       //.. except the shift key which is NOT part of the matrix
        if (keyboard_getshift())
          thisScancode |= KEYBOARD_SHIFT;
        if (thisScancode != lastScancode)
        {
          //printf(&quot;Scan: %d\r\n&quot;,thisScancode);
          fifo_put(&amp;keyfifo, thisScancode);
        //this is typematic. to generate multiple keystrokes on one single looooooooooong press
#ifdef ENABLE_TYPEMATIC
          typematicCnt=0;
#endif
        }
#ifdef ENABLE_TYPEMATIC
        else
        {
          typematicCnt++;
          if ((typematicThreshold+typematicSpeed)&lt;=typematicCnt)
          typematicCnt=typematicThreshold;

          if (typematicThreshold==typematicCnt)
          {
            fifo_put(&amp;keyfifo, thisScancode);
          }
        }
#endif
      }
      lastScancode = thisScancode;
      //Now we have to do the processing because we get some freshly debounced situation, baby!
      //currentKey=((thisScan^oldScan)&amp;thisScan);
      //oldScan=thisScan;
    }
    lastScan = thisScan;
    thisScan = 0;
  }
}

//that's it, folks ;)
```

## 迪安·霍尔的去抖代码

AVR 微控制器上的去抖引脚中断

```
/*
 * Sample debouncing code
 *
 * Copyright 2010 Dean Hall.
 * This code snippet is offered under the MIT license:
 * http://www.opensource.org/licenses/mit-license.html
 */

/*
 * The hardware is an AVR with a switch connected to the INT0 input.
 * The firmware uses:
 *
 * - AVR Libc: http://www.nongnu.org/avr-libc/
 * - The AvrX microkernel: http://www.barello.net/avrx/
 *
 * This sample code performs debouncing on the INT0 input.
 * Here is the expected sequence of actions:
 *
 * - The AVR can be doing anything (awake or asleep) when the button is pressed
 * - The button press produces a low-going signal and bounces for a time
 * - The low-going signal activates the INT0 interrupt
 * - The INT0 service routine:
 *     - Disables the INT0 interrupt so bouncing doesn't cause multiple IRQs
 *     - Puts an AvrX message in the event queue of the inputs task
 * - The event in the queue causes the inputs_task to be scheduled, which:
 *     - Performs the action that the INT0 button is supposed to invoke
 *     - Starts an AvrX delay timer to allow for the button to stop bouncing
 *       During this delay, other AvrX tasks may run.
 *     - After the delay, the INT0 interrupt is re-enabled for the next input.
 *
 * In this design, the delay is especially long (1s) due to a very cheap button
 * and no need to respond to fast button presses.
 *
 * The downside of this software design is that no other input events are
 * processed while a button is debounced, although their press-messages are
 * queued up and handled after the debounce period.  This behavior was
 * acceptable for this immediate design, but may not be for all situations.
 */

#include &lt;avr/interrupt.h&gt;
#include &quot;avrx.h&quot;

#define DEBOUNCE_DELAY (uint16_t)(1000 / MILLISECONDS_PER_TIC)

static MessageControlBlock remote_ctrl_pressed_msg;

/* Remote Control button press interrupt service routine */
AVRX_SIGINT(INT0_vect)
{
   IntProlog();

   /* Disable INT0/RemoteCtrl interrupt */
   GICR &amp;= ~_BV(INT0);

   AvrXIntSendMessage(&amp;inputs_msg_queue, &amp;remote_ctrl_pressed_msg);
   Epilog();
}

AVRX_GCC_TASKDEF(inputs_task, TASK_STACK_SIZE, 3)
{
   TimerControlBlock debounce_timer;
   MessageControlBlock *pmsg;

   /* Set INT0/RemoteCtrl and INT1/OpTest to trigger on falling edge */
   GICR &amp;= ~(_BV(INT0) | _BV(INT1));
   MCUCR &amp;= ~(_BV(ISC00) | _BV(ISC10));
   MCUCR |= (_BV(ISC01) | _BV(ISC11));
   GICR |= (_BV(INT0) | _BV(INT1));

   /* ... other initialization stuff removed */

   for (;;)
   {
       /* Wait for a message that an input was pressed or timer expired */
       pmsg = AvrXWaitMessage(&amp;inputs_msg_queue);

       /* ... removed if-cases for other unrelated input messages */

       else if (pmsg == &amp;remote_ctrl_pressed_msg)
       {
           DEBUG_PRINT(VERBOSITY_LOW, &quot;RmtCtrl pressed.\n&quot;);

           /* ... removed code that performs the action the button invokes */

           /* Debounce delay for RemoteCtrl button; lets other threads run */
           AvrXDelay(&amp;debounce_timer, DEBOUNCE_DELAY);

           /* Clear flag and enable interrupt */
           GIFR |= _BV(INTF0);
           GICR |= _BV(INT0);
       }
   }
}

```

## 布拉德·巴斯勒的去抖代码

使用 ISR 同步或异步去抖。用法在[本线程](http://www.avrfreaks.net/index.php?name=PNphpBB2&file=viewtopic&index&t=89686)中讨论。

去抖 h:

```
#ifndef __DEBOUNCE_H__
#define __DEBOUNCE_H__

#include &lt;avr/interrupt.h&gt;

//Optimized for 20 millisecond period on a 1Mhz clock
#define DBNC_TIMR0_PRESCALER 	_BV(CS02)
#define DBNC_TIMR0_BASEVAL	 	178

//Defines the size of the debouncer handler arrays (i.e. 4 for a maximum of four)
#define DBNC_NUM_DEBOUNCERS		8

//Defines the number of timer ticks before a value is considered legitimate
//This will define a maximum debounce time of approx 100 milliseconds @ 5
//The minimum debounce time will be approx 80 milliseconds
#define DBNC_COUNTER_TOP 3

#define _BITSHIFTBY(bit,num) ((bit)&lt;&lt;(num))

typedef void(*debounceHandler)(uint8_t,uint8_t);

typedef struct
{
	//A pointer to a volatile port (I/O or otherwise)
	volatile uint8_t *port;

	//A pointer to a debounceHandler function
	debounceHandler handler;

	//This is the decremental counter which determines
	//if the button has been debounced
	uint8_t counter;

	/*

		Bits 0-3: bit index to check against (0-7)
		Bits 4-5: unused
		Bit    5: Last known sate
		Bit    6: Signaled
		Bit    7: Asynchronous

	*/
	uint8_t bitmap;
} DBNC_ITEM;

typedef struct
{

	//An array of debouncer units
	DBNC_ITEM dbUnits[DBNC_NUM_DEBOUNCERS];

	//This is set to 1 when any signal in the dbncSignaled array has been set
	uint8_t signalReady;

} DBNC_GLOBAL;

/*
	Forward Declarations
*/

//ISR for timer0 overflow interrupt
ISR(TIMER0_OVF_vect);
void callSignaledHandlers(void);
void registerDebouncer(volatile uint8_t *port,uint8_t bit,uint8_t index,uint8_t Asynchronous,debounceHandler handler);
void signalChangedState(uint8_t index,uint8_t counterTop);
void initializeDebouncerTimer();

#endif

```

去抖 c:

```
#include &lt;avr/io.h&gt;
#include &lt;avr/interrupt.h&gt;
#include &lt;util/delay.h&gt;
#include &quot;debounce.h&quot;

volatile DBNC_GLOBAL db;

//ISR for timer0 overflow interrupt
ISR(TIMER0_OVF_vect)
{
	uint8_t i;
	uint8_t temp;
	uint8_t workDone = 0;

	//Cycle through all debounced items
	for (i=0;i&lt;DBNC_NUM_DEBOUNCERS;i++)
	{
		//Skip items that have been idle
		if (db.dbUnits[i].counter == 0)
			continue;

		workDone = 1;

		//If debounce period has elapsed
		if (--db.dbUnits[i].counter == 0)
		{

			//Grab current logical bit state of the port (1 or 0)
			temp = (((*(db.dbUnits[i].port)) &amp; _BV((db.dbUnits[i].bitmap &amp; 0b111))) != 0);

			//If current state != last state
			//store change
			if (temp != ((db.dbUnits[i].bitmap &amp; _BV(5)) &gt;&gt; 5))
			{
				//Flip last state bit
				db.dbUnits[i].bitmap ^= _BV(5);

				//If this debouncer item is synchronous
				//Then signal it
				if (!(db.dbUnits[i].bitmap &amp; _BV(7))) {

					//Signal this debouncer item
					db.dbUnits[i].bitmap |= _BV(6);

					//Signaling options
					db.signalReady = 1;
				}

				//Otherwise it's asynchronous,
				//call immediately
				else
					//Call Handler
					(*db.dbUnits[i].handler)(i,temp);
			}
		}
	}

	//If all counters were already 0, disable the timer
	if (!workDone)
		TCCR0B = 0;

	TCNT0  = DBNC_TIMR0_BASEVAL;
}

//Call any signaled handlers (to be executed in main program loop)
void callSignaledHandlers(void)
{
	int i;

	if (!db.signalReady) return;

	for (i=0;i&lt;DBNC_NUM_DEBOUNCERS;i++)
	{
		//Check if this item is signaled
		if (db.dbUnits[i].bitmap &amp; _BV(6)) {

			//If so, reset its signal
			db.dbUnits[i].bitmap &amp;= ~_BV(6);

			//Call item and pass on last known state
			(*db.dbUnits[i].handler)(i,(db.dbUnits[i].bitmap &amp; _BV(5))&gt;&gt;5);
		}
	}

	//Reset signal
	db.signalReady = 0;

}

void registerDebouncer(volatile uint8_t *port,uint8_t bit,uint8_t index,uint8_t Asynchronous,debounceHandler handler)
{
	//Store port pointer
	//Store handler pointer
	//Reset counter to 0
	//Store bitmap of bit offset/asynchronous state
	//Set signaled to 0
	db.dbUnits[index].port 		= port;
	db.dbUnits[index].handler 	= handler;
	db.dbUnits[index].counter  	= 0;

	db.dbUnits[index].bitmap	= _BITSHIFTBY((Asynchronous != 0),7)|
						 		  _BITSHIFTBY((((*port) &amp; _BV(bit)) != 0),5)|
						 		  bit;
}

void signalChangedState(uint8_t index,uint8_t counterTop)
{
	if (!counterTop)
		db.dbUnits[index].counter = DBNC_COUNTER_TOP;
	else
		db.dbUnits[index].counter = counterTop;

	if (!TCCR0B)
		TCCR0B = DBNC_TIMR0_PRESCALER;
}

void initializeDebouncerTimer()
{
	//Note: doesn't start timer
	TCCR0A = 0x00;
	TCCR0B = 0x00;
	TCNT0  = DBNC_TIMR0_BASEVAL;
	TIMSK0 = _BV(TOIE0);
}

```

测试. c:

```
#include &lt;avr/io.h&gt;
#include &lt;util/delay.h&gt;
#include &quot;debounce.h&quot;

volatile uint8_t lastState;

void ButtonClicker(uint8_t index,uint8_t state);

/*

Pin-change interrupt 0

	Detects pin changes on PCINT0-7 (all masked on), i.e. PB0-7 on Atmega2560

	It compares these values to the last known state and signals a change
	on any pins that have changed state.

*/
ISR(PCINT0_vect)
{
	uint8_t temp = lastState^PINB;
	lastState = PINB;

	if ((temp &amp; _BV(0)))
		signalChangedState(0,2);
	if ((temp &amp; _BV(1)))
		signalChangedState(1,3);
	if ((temp &amp; _BV(2)))
		signalChangedState(2,4);
	if ((temp &amp; _BV(3)))
		signalChangedState(3,5);
	if ((temp &amp; _BV(4)))
		signalChangedState(4,20);
	if ((temp &amp; _BV(5)))
		signalChangedState(5,50);
	if ((temp &amp; _BV(6)))
		signalChangedState(6,200);
	if ((temp &amp; _BV(7)))
		signalChangedState(7,200);
}

int main(void)
{
	//Initialize PORTB as all inputs, no internal pull-ups
	DDRB  = 0x00;
	PORTB = 0x00;

	//Initialize PORTD as all outputs, all HIGH (LEDs off)
	DDRD  = 0xFF;
	PORTD = 0xFF;

	//Initial timer setup (does not start timer)
	initializeDebouncerTimer();

	lastState = PINB;

	//Fills in details regarding
	registerDebouncer(&amp;PINB,PB0,0,1,&amp;ButtonClicker);
	registerDebouncer(&amp;PINB,PB1,1,1,&amp;ButtonClicker);
	registerDebouncer(&amp;PINB,PB2,2,1,&amp;ButtonClicker);
	registerDebouncer(&amp;PINB,PB3,3,1,&amp;ButtonClicker);
	registerDebouncer(&amp;PINB,PB4,4,0,&amp;ButtonClicker);
	registerDebouncer(&amp;PINB,PB5,5,0,&amp;ButtonClicker);
	registerDebouncer(&amp;PINB,PB6,6,0,&amp;ButtonClicker);
	registerDebouncer(&amp;PINB,PB7,7,0,&amp;ButtonClicker);

	//Enable pin-change interrupt &amp; mask
	PCICR  = _BV(PCIE0);
	PCMSK0 = 0xFF;

	//Enable interrupts
	sei();

	while(1)
	{
		//This will loop through any signaled debouncer items and
		//call their handlers (doesn't apply to asynchronous)
		callSignaledHandlers();

		_delay_ms(5);
	}

	return 0;
}

void ButtonClicker(uint8_t index,uint8_t state)
{
	if (state == 0)
	{

		PORTD ^= _BV(index);
	}
}

```

## 威廉·狄龙的去抖代码

使用软件中的上升沿和下降沿检测来创建数字滤波器。

```
/* uint8_t doDebounce(uint8_t *state, volatile uint8_t *port, uint8_t pin)
 *
 * This function implements the logic for detecting button transitions for
 * arbitrary ports and bits.  The return value is the debounced value the the
 * given pin.
 *
 * The implementation of this function is inspired by the digital filter
 * presented in ECE573 at Oregon State University.  It is different because
 * I'm using the single 8-bit variable to store all of the state, rather than a
 * 8 bit accumulator and 8 bit flag.  We're using the range from 0x00 -&gt; 0x7F
 * and bit 7 (0x80) as the flag.
 *
 * The user of this function must provide a static state variable.  This
 * value encodes the state and history of the pin  Failure to maintain the state
 * would cause erratic behavior.  The port can be any of the PINn
 * memory-mapped input buffers.  Pin must be between 0 and 7.
 *
 * Because these buttons pull to ground, we'll invert the meaning of the edges
 * in software, 1 = yes is much more natural.
 */
uint8_t doDebounce(uint8_t *state, volatile uint8_t *port, uint8_t pin) {
       uint8_t old  =  *state &amp; 0x7F;
       uint8_t flag = (*state &amp; 0x80)? 1 : 0;

       // Digital filter part, value = (old * .75) + (new * .25)
       old -= (old &gt;&gt; 2);                                                              // 1 - (1/4) = .75
       old += ((*port) &amp; (1 &lt;&lt; pin))? 0x1F : 0x00;             // if bit set, add .25

       // Software schmitt trigger
       // Newly detected rising edge
       if ( (flag == 1) &amp;&amp; (old &gt; 0x70) ) {
               flag = 0;
       }

       // Newly detected falling edge
       else if ( (flag == 0) &amp;&amp; (old &lt; 0x07) ){
               flag = 1;
       }

       // Update the state variable
       *state = (old &amp; 0x7F) | ((flag &amp; 0x01) &lt;&lt; 7);

       // Return only the pin state
       return flag;
}
```

## Mike Szczys 的去抖代码

我很早就爱上了丹尼去抖代码。这是我修改后的版本。

```
/*--------------------------------------------------------------------------
10/13/2010: Button debounce code by Mike Szczys

based on &quot;danni debounce&quot; code by Peter Dannegger:

http://www.avrfreaks.net/index.php?name=PNphpBB2&file=viewtopic&p=189356#189356

This code detects and debounces button presses. It is tailored for use with
AVR microcontrollers but I've adapted it for other architectures easily and
successfully. It can be modified to use all eight bits on the same port
for up to eight buttons.

The interrupt service routine (ISR) at the bottom uses binary counter
variables (ct0 and ct1) to check the buttons once every 10ms until 40ms has
passed. If the button registeres the first and last times it reads it as
a keypress. There is no functionality in this code for detecting a held
button.
--------------------------------------------------------------------------*/

// F_CPU used by debounce to calculate 10ms interrupts
#define F_CPU 1200000

#include &lt;avr/io.h&gt;
#include &lt;avr/interrupt.h&gt;

//define pins used by buttons
#define KEY_DDR		DDRB
#define KEY_PORT	PORTB
#define KEY_PIN		PINB
#define KEY0		1	//Button on PB1
#define KEY1		2	//Button on PB2

//Debounce variables
unsigned char debounce_cnt = 0;
volatile unsigned char key_press;
unsigned char key_state;

/*--------------------------------------------------------------------------
  Prototypes
--------------------------------------------------------------------------*/
unsigned char get_key_press( unsigned char key_mask );
void init_timers(void);
void init_io(void);

/*--------------------------------------------------------------------------
  FUNC: 10/13/10 - Used to read debounced button presses
  PARAMS: A keymask corresponding to the pin for the button you with to poll
  RETURNS: A keymask where any high bits represent a button press
--------------------------------------------------------------------------*/
unsigned char get_key_press( unsigned char key_mask )
{
  cli();			// read and clear atomic !
  key_mask &amp;= key_press;	// read key(s)
  key_press ^= key_mask;	// clear key(s)
  sei();			// enable interrupts
  return key_mask;
}

/*--------------------------------------------------------------------------
  FUNC: 10/13/10 - Sets and starts a system timer
  PARAMS: NONE
  RETURNS: NONE
--------------------------------------------------------------------------*/
void init_timers(void)
{
  cli();			// read and clear atomic !
  //Timer0 for buttons
  TCCR0B |= 1&lt;&lt;CS02 | 1&lt;&lt;CS00;	//Divide by 1024
  TIMSK0 |= 1&lt;&lt;TOIE0;		//enable timer overflow interrupt
  sei();			// enable interrupts
}

/*--------------------------------------------------------------------------
  FUNC: 10/13/10 - Initialize input and output registers
  PARAMS: NONE
  RETURNS: NONE
--------------------------------------------------------------------------*/
void init_io(void)
{
  //Setup Buttons
  KEY_DDR &amp;= ~((1&lt;&lt;KEY0) | (1&lt;&lt;KEY1));	//Set pins as input
  KEY_PORT |= (1&lt;&lt;KEY0) | (1&lt;&lt;KEY1);	//enable pull-up resistors
}

/*--------------------------------------------------------------------------
  FUNC: 10/13/10 - Main
--------------------------------------------------------------------------*/
int main(void)
{
  init_timers();	//start the timer
  init_io();		//setup the buttons

  for (;;) //loop forever
  {
    if( get_key_press( 1&lt;&lt;KEY0 ))
    {
      //KEY0 press detected. Do something here
    }

    if (get_key_press( 1&lt;&lt;KEY1 ))
    {
      //KEY1 press detected. Do something here
    }
  }
}

//--------------------------------------------------------------------------
ISR(TIM0_OVF_vect)           // interrupt every 10ms
{
  static unsigned char ct0, ct1;
  unsigned char i;

  //TCNT0 is where TIMER0 starts counting. This calculates a value based on
  //the system clock speed that will cause the timer to reach an overflow
  //after exactly 10ms
  TCNT0 = (unsigned char)(signed short)-(((F_CPU / 1024) * .01) + 0.5);   // preload for 10ms interrupts

  i = key_state ^ ~KEY_PIN;    // key changed ?
  ct0 = ~( ct0 &amp; i );          // reset or count ct0
  ct1 = ct0 ^ (ct1 &amp; i);       // reset or count ct1
  i &amp;= ct0 &amp; ct1;              // count until roll over ?
  key_state ^= i;              // then toggle debounced state
  key_press |= key_state &amp; i;  // 0-&gt;1: key press detect
}
```

链接到其他代码

有些人刚刚给我们发来了代码链接。他们在这里:

【彼得·康拉迪】矩阵扫描码。

[Hernandi f . kram mes '][PIC 的去抖代码](http://formfeed.blogspot.com/2010/10/debounce-machine-i-state-approach.html)。

[戴夫]使用[杰克·甘斯勒的]去抖码；本页面的[清单 2。](http://www.ganssle.com/debouncing-pt2.htm)

[图片来源:[杰克·甘斯勒](http://www.ganssle.com/debouncing.htm)