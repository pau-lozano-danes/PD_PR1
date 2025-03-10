#include <Arduino.h>
#include <Adafruit_NeoPixel.h>

#define BUTTON_PIN  0   // Pin del botón (ajustar según tu hardware)
#define LED_PIN     48  // Pin del LED RGB integrado (cambia según la placa)
#define NUM_LEDS    1   // Solo hay un LED RGB

Adafruit_NeoPixel strip(NUM_LEDS, LED_PIN, NEO_GRB + NEO_KHZ800);

bool ledState = false;  // Estado del LED (apagado al inicio)
bool lastButtonState = false;
unsigned long lastDebounceTime = 0;
const unsigned long debounceDelay = 50;

void setup() {
    pinMode(BUTTON_PIN, INPUT_PULLUP);  // Configura el botón con resistencia interna
    strip.begin();
    strip.show();  // Apaga el LED al inicio
}

void loop() {
    bool reading = !digitalRead(BUTTON_PIN);  // Lee el botón (invertido por pull-up)

    if (reading != lastButtonState) {
        lastDebounceTime = millis();
    }

    if ((millis() - lastDebounceTime) > debounceDelay) {
        if (reading != lastButtonState) {
            lastButtonState = reading;

            if (reading) {  // Si se presiona el botón, cambia el estado del LED
                ledState = !ledState;

                if (ledState) {
                    strip.setPixelColor(0, strip.Color(255, 255, 255));  // LED Blanco
                } else {
                    strip.setPixelColor(0, strip.Color(0, 0, 0));  // Apagar LED
                }
                strip.show();
            }
        }
    }
}
