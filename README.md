# Project IGOR - open-source, loyal, cheerful assistant

> [!TIP]  
> This is the base configuration of IGOR, to serve one straight forward, important use case: it turns the IGOR platform into a simple and effective focus assistant (simple by design). It works very well as is.
> 
> However, if you wish, you can go beyond this and make this human-machine/ human-computer interface truly your own.
>
> The hardware is capable, the minimalist design is tactile + satisfying to use, and the firmware is easy to develop/ scale in whichever direction your imagination leads you towards!
> I'm excited to see what you come up with!

Base IGOR: A simple, tactile tool to help you track and hopefully increase the amount of minutes that matter each day.

This project is designed to help you stay on track with your focus sessions, using a simple and intuitive interface via a rotary encoder and an OLED display. Whether you need to time focused work, breaks or other worthy pursuits, this simple cheerful timer is a perfect tool to support your productivity.

Bonus: it's cheap to put together and highly hackable. I wrote the code in a modular way and you can add your own functions to it easily. Just make sure you share that back so that we can all enjoy your ideas in action!!

## Its simple features (v1)

- **Up and Down Counting Modes:** Select either *count up* or *count down* mode. Both are in minutes based on millies (seconds seem way too distracting - you want to slow down and dive in).
- **Rotary Encoder Control:** Use the encoder to navigate the menu and adjust timer values. Rotate to move up and down, click to confirm. Easy.
- **OLED Display:** Provides real-time feedback on timer status and focus session duration, as well as your beautiful Flow total minutes acculturated since your last reset.
- **IDLE Mode:** Automatically enters *IDLE mode* after 3 minutes of inactivity (and shows up a question to prompt you to come back into action), turns off the display after 30 minutes to conserve energy.
- **Success Animation:** Displays a short animation at the end of each session (positive reinforcement gains!).
- **Manual Timer Reset:** Reset your total focus time using a simple menu option so you can start afresh. Unplugging the device also achieves this - nothing is permanent, we have to keep performing!
- **Cute hats that you can swap:** Design your own rotary encoder knobs, ney - hats, or download some that I made. Add some personality to your assistant, be it a British butler, a French concierge, or Italian enforcer, etc. have some fun with this. And make sure you give it a name.

![_DSC0945 Large](https://github.com/user-attachments/assets/ef5a7adf-0809-4d12-9821-14966fce223a)

## Sound notification (v1.5)
- **Sound notification:** small and customizable sound notifications that play with every click and at the end of any focus/break session. Sound notifications can be disable from the menu.

Requires a piezo buzzer (PS1240, SFM-27 or any type) available on every amazon in set ~3-6 $/£/€
| Component            | Pin | Wiring| 
|----------------------|-----|-------------|
| Buzzer    		   | D8  | Connect one pin to D8 and the other to GND


## BOM

- Adafruit SSD1306 OLED Display (128x64)
- KY-040 rotary encoder
- D1 mini board (any Arduino board will do, but you will have to adjust the sketch)
- 3D printer for the shell - all pressure fit, no screws, no glue, nothing else required

Affiliate links to grab the components (if you want to use them):

| Component       | Amazon US Link                     | Amazon UK Link                     |
|---------------|--------------------------------|--------------------------------|
| Rotary Encoder | https://amzn.to/4h4bjCB | https://amzn.to/432Xb8A |
| OLED Display  | https://amzn.to/4apCANs | https://amzn.to/4gYGKxk |
| Microcontroller (USB-C D1 Mini) | https://amzn.to/4h2zQYO | https://amzn.to/4gRFgFe |

(unit cost at the time of writing: just under $7. I'd recommend buying the components in sets - they're great for many projects, and the sets drives the unit cost down)

**Note:** in case you have a **Pico** around already, you can use that variant as the basis for your IGOR thanks to one of our contributors! Pico code in repo.

## Pinout

| Component            | Pin |
|----------------------|-----|
| OLED SDA             | D2  |
| OLED SCL             | D1  |
| Rotary Encoder CLK   | D6  |
| Rotary Encoder DT    | D7  |
| Rotary Encoder SW    | D4  |

## Wiring (for illustration - always check your actual components vs firmware)

![image](https://github.com/user-attachments/assets/37c8985d-d737-4752-ad43-fd7bf724d4a1)

## Microcontroller firmware

One sketch file, using the IDE of your choice (e.g. the main Arduino IDE works well with the added modules for D1 mini + libraries - that's what I use).  
Please check everything is working before soldering and squeezing everything into the 3D printed shell.

## Assembly

There are only 3 components to this:

- The shell - the D1 mini fits snuggly in there, and the rotary encoder screws on the top.
- The faceplate - the OLED slides in (make sure the display is nicely squared - the slide should allow some wiggle room, as the tolerances on these displays are quite bad but hey, it's really cheap).
- The hat - this is the knob to rotate and press on. It fits on top of the rotary encoder, with the key as a guide.

The orientation of parts on the printer's bed matters - only some hats will need internal supports because of the interface with the rotary encoder. All else prints easily with normal PLA (but you can get more exotic - people share your creations!).

Do play with the dimensions - tolerances (around 0.2-0.3mm) work very well for our printers and achieve a satisfying fit, but they require some adjustment/scaling for your setup.

The order of the assembly I found to work best is:

1. First, wire everything together, write the firmware to the board, fire it up, rotate, click, play - make sure everything works well. Do not use headers for the D1 mini, check the length of your wires and the orientation of components - it's a tight but precise fit.
2. Second, the OLED panel should be attached to the faceplate.
3. Third, the rotary encoder and the D1 mini (which only goes in one way) should be attached to the shell.
4. Lastly, you can snap everything together.

Note on hats: I encourage you to make this your own by designing and printing (and hopefully sharing) a custom hat. The dimensions to fit the encoder are openly available online and it's really simple to put something together. I have made available several iteration that I found funny or relevant as I was dressing up my assistant - you only need one.

## User Guide

### How to Use

#### 1. Initial Setup

When powered on, the device will start in the main menu. The top of the screen displays your total focus time, while the main menu shows the current option to select (UP, DOWN, or Reset). The rotary encoder allows you to scroll through the options and make selections with a button press.  
Basically, there is no initial setup... we're ready when you are!

#### 2. Main Menu

The main menu offers four options:

- **UP:** Start counting focus time upward. Great for open-ended focus sessions.
- **DOWN:** Select a countdown duration and track your focus session as it counts down to zero.
- **Reset:** Manually reset your total focus time to zero. This won't affect current sessions but will clear the accumulated flow minutes shown on the top of the screen.
- **Volume on/off: (1.5v)** Enable or disable sound notification for click, open and focused session.

#### 3. Count UP Mode

- Rotate to the **UP** option and click the button to start.
- The display shows "Focus!" with an upward-pointing triangle, and the elapsed minutes appear in large text.
- Click the button again to stop and return to the menu. The session's duration is added to your total focus time.

#### 4. Count DOWN Mode

- Rotate to the **DOWN** option and click the button.
- Use the encoder to adjust the countdown duration, then click again to start the countdown.
- The display shows "Focus!" with a downward-pointing triangle, and the remaining minutes appear in large text.
- When the countdown reaches zero, a success animation is displayed, and the time is added to your total focus time.

#### 5. Reset Focus Time

From the menu, rotate to the **Reset** option and click the button to reset your total focus time to zero.

#### 6. IDLE Mode

If the timer remains in the menu or selection screen without user interaction for more than 3 minutes, the display will show "IDLE?" - this is purely to taunt you back into action!  
After 30 minutes of inactivity, the display turns off entirely - this is to conserve energy.  
Simply press the button to exit IDLE mode and return to the menu.

#### 7. Sound notification (v1.5)
Sound can be enabled or disabled for the related option in the menu. It's possible to customize sounds used for click, open and focused session directly from the script, specifying note and their duration. Sounds can be created directly online with tool such as https://tone-maker.vercel.app/. Other useful links for sounds creation:
* https://docs.arduino.cc/built-in-examples/digital/toneMelody/ 
* https://github.com/robsoncouto/arduino-songs

### Example Workflow

- Select **UP** to start timing a work session.
- After completing the session, stop the timer, and your total focus time is updated.
- Next, select **DOWN** to time a 20-minute break by adjusting the countdown timer.
- At the end of the day, if you want to reset your total focus time, navigate to **Reset** and click the button to start fresh.

## Video showcasing the whole thing
https://youtu.be/Wko0zgRGtPI

## Roadmap ideas

Here are a bunch of features I think might be cool to try out. Please add your ideas as well. Also, please help me by submitting code!! I'm a designer, not a programmer and could really use some of your talents to bring this project alive.

- [X] Add sound notifications
- [ ] Get internet time via Wifi + portal, since this is a ESP module
- [ ] More animations and transitions
- [ ] More modes available (any ideas?)
- [ ] API to interact with external applications (e.g. Time trackers, ToDo apps, Shortcuts/ automations)

## Disclaimer

I've done my best to document everything accurately - however, there might be mistakes. If you see them, or opportunities to improve, please open an issue.  
This is an open-source project given for free, with no warranties or guarantees. It assumes a level of proficiency with electronics, assemblies, engineering, etc. Stay safe. Stay productive. Work with what you have. Make the world a better place.
