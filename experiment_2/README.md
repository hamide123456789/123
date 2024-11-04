## موضوع آزمایش:سنسور دنده عقب
### گزارش کار

سنسور دنده عقب در خودروها نوعی هشدار دهنده می باشد به صورتی که در هنگام دنده عقب رفتن خودرو به طور اتوماتیک فعال می شود و اگر که فاصله خودرو تا یک مانع که در پشت آن قرار دارد از یک اندازه مشخصی کمتر شود ( حدودا یک متر ) سنسور شروع به هشدار دادن از طریق صدا می کند به صورتی که هر چقدر خودرو به مانع نزدیک تر شود شدت این آلارم بیشتر خواهد شد.  
ما نیز در مدار یک LED قرار می دهیم و می خواهیم در محدوده بین 4 تا 30 سانتی متری از اولتراسونیک هر مانعی قرار گرفت LED روشن شود البته به شکلی که هر اندازه جسم به سنسور نزدیک تر شد شدت روشنایی نور LED بیشتر شود و بلعکس.

---

### کدبرنامه

```cpp
int trig = 10;
int echo = 9;
int duration = 0;
int distance = 0;
int led = 11;
int pwmLed = 0;

void setup() {
  pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);
  pinMode(led, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  digitalWrite(trig, LOW);
  delayMicroseconds(2);
  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);

  duration = pulseIn(echo, HIGH);
  distance = (duration / 2) * 0.0343;

  analogWrite(led, 0);
  if (distance >= 4 && distance <= 30) {
    pwmLed = map(distance, 4, 30, 255, 0);
    analogWrite(led, pwmLed);
    Serial.println(distance);
    delay(100);
    }

    Serial.println(distance);
    delay(100);
}
```
### تصویر مدار

![pic micro](/pic/microprocessor2.jpg)

---

### شماتیک مدار 

![pic schematic](/pic/schematic_11.jpg)


