/* ## loadcell
## How to calibrate your load cell
1. Call `set_scale()` with no parameter.
2. Call `tare()` with no parameter.
3. Place a known weight on the scale and call `get_units(10)`.
4. Divide the result in step 3 to your known weight. You should
   get about the parameter you need to pass to `set_scale()`.
5. Adjust the parameter in step 4 until you get an accurate reading.
   */
#include "HX711.h"


// HX711 circuit wiring
const int LOADCELL_DOUT_PIN = 2;
const int LOADCELL_SCK_PIN = 3;


HX711 scale;

void setup() {
  Serial.begin(38400);
  Serial.println("HX711 Demo");
  Serial.println("Initializing the scale");
  scale.begin(LOADCELL_DOUT_PIN, LOADCELL_SCK_PIN);
  scale.set_scale();
  scale.tare();    
}

  void loop() {
  Serial.println(""Put known weight on the scale"");
  delay(10000);
  Serial.println(scale.get_units(10));
  delay(10000);    
  }
