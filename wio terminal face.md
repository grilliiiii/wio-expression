# Wio Terminal expression showing

<div align=center><img width = 500 src="https://files.seeedstudio.com/wiki/Wio-Terminal/img/wiotermianl_stand.jpg"/></div>

This example demomstrates how to display the expression from Wio Terminal

## Getting Started

### Materials Required

- Wio Terminal

<div align=center><img width = 800 src="https://media-cdn.seeedstudio.com/media/catalog/product/cache/b5e839932a12c6938f4f9ff16fa3726a/0/0/0072.jpg"/></div>

### Step 1. Pull up the Configurable Buttons

>**Note**: `WIO_KEY_A`, `WIO_KEY_B` and `WIO_KEY_C` are defined for the Wio Terminal configurable buttons.

```c++
void setup()
{
   pinMode(WIO_KEY_A, INPUT_PULLUP);
   pinMode(WIO_KEY_B, INPUT_PULLUP);
   pinMode(WIO_KEY_C, INPUT_PULLUP);
}
```

### Step 2. Initialize the TFT LCD Screen

To initialise the TFT LCD screen on Wio Terminal,and to display the sentence: Wio terminal is funny ! !

```c++
#include"TFT_eSPI.h"

TFT_eSPI tft;
 
void setup() 
{
  ...
  tft.begin();
  tft.setRotation(3);
  tft.fillScreen(TFT_BLACK); // Fills the screen with BLACK background
  tft.setTextColor(TFT_GREEN); // sets the text colour to green
  tft.setTextSize(2);
  tft.drawString("Wio terminal is funny ! !", 15, 90); // prints strings from (15, 90)
  ...
}
```

### Step 3. Draw Character and Text Strings

- To draw `Character` on TFT LCD screen.

```c++
void loop()
{
    tft.fillScreen(TFT_BLACK); // BLACK background
    tft.drawChar(90, 90, '>', TFT_GREEN, TFT_GREEN, 4);  // Draw a green character A from (90,90)
    tft.drawChar(210, 90, '<', TFT_GREEN, TFT_GREEN, 4); // Draw a green character B from (210,90)
}
```

- To draw `Text Strings` on TFT LCD screen.

<img src="x.jpg" width="800"/>

```c++
void loop()
{
    tft.fillScreen(TFT_BLACK);   // BLACK background
    tft.setTextColor(TFT_GREEN); // sets the text colour to green
    tft.setTextSize(4);
    tft.drawString("X    X ", 95, 90); // prints strings from (95, 90)
}
```

### Step 4. Use if statement to select the expression

```c++
if (digitalRead(WIO_KEY_A) == LOW){...}
```

### Example code

```c++
#include <Arduino.h>
#include "TFT_eSPI.h"

TFT_eSPI tft;

void setup()
{

   pinMode(WIO_KEY_A, INPUT_PULLUP);
   pinMode(WIO_KEY_B, INPUT_PULLUP);
   pinMode(WIO_KEY_C, INPUT_PULLUP);

   tft.begin();
   tft.setRotation(3);
   tft.fillScreen(TFT_BLACK);                           // Fills the screen with BLACK background
   tft.setTextColor(TFT_GREEN);                         // sets the text colour to green
   tft.setTextSize(2);
   tft.drawString("Wio terminal is funny ! !", 15, 90); // prints strings from (15, 90)
}

void loop()
{

   if (digitalRead(WIO_KEY_A) == LOW)
   {

      tft.fillScreen(TFT_BLACK);                           // BLACK background
      tft.drawChar(90, 90, '>', TFT_GREEN, TFT_GREEN, 4);  // Draw a green character A from (90,90)
      tft.drawChar(210, 90, '<', TFT_GREEN, TFT_GREEN, 4); // Draw a green character B from (210,90)
   }
   else if (digitalRead(WIO_KEY_B) == LOW)
   {
      tft.fillScreen(TFT_BLACK);         // BLACK background
      tft.setTextColor(TFT_GREEN);       // sets the text colour to black
      tft.setTextSize(4);
      tft.drawString("0    0 ", 95, 90); // prints strings from (95, 90)
   }
   else if (digitalRead(WIO_KEY_C) == LOW)
   {
      tft.fillScreen(TFT_BLACK);         // BLACK background
      tft.setTextColor(TFT_GREEN);       // sets the text colour to green
      tft.setTextSize(4);
      tft.drawString("X    X ", 95, 90); // prints strings from (95, 90)
   }
} 
```

## Tech support

Please submit any technical issues into our [forum](https://forum.seeedstudio.com/)<br /><p style="text-align:center"><a href="https://www.seeedstudio.com/act-4.html?utm_source=wiki&utm_medium=wikibanner&utm_campaign=newproducts" target="_blank"><img src="https://files.seeedstudio.com/wiki/Wiki_Banner/new_product.jpg" /></a></p>
