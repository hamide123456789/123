# موضوع آزمایش امواج فراصوت 

## گزارش کار 
سنسورهای اولتراسونیک دو بخش دارند: فرستنده و گیرنده. فرستنده سیگنال فراصوتی ارسال می‌کند که اگر به مانع برخورد کند و برگردد، گیرنده آن را دریافت می‌کند و زمان رفت و برگشت را محاسبه می‌کند. با استفاده از سرعت صوت (340 متر بر ثانیه) و فرمول زیر می‌توان فاصله را محاسبه کرد:

فاصله = (زمان رفت و برگشت / 2) * سرعت صوت

---

### کد بر نامه

```cpp
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 7, 6, 5, 4);
int trig = 10;
int echo = 9;
int duration = 0;
int distance = 0;

void setup() {
  lcd.begin(16, 2);
  pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);
}

void loop() {
  digitalWrite(trig, LOW);
  delayMicroseconds(2);
  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);

  duration = pulseIn(echo, HIGH);
  distance = (duration / 2) * 0.0343;

  lcd.print("Distance = ");
  lcd.setCursor(11, 0);
  lcd.print(distance);
  delay(500);
  lcd.clear();
}
```

### شرح کارکرد مدار به صورت ویدیویی 🎥

<br>

<div align="center">
<img src="/pic/microprocessor1.jpg">
</div>

---

### شماتیک مدار 🗺️

<br>

<div align="center">
<img src="/media/schematic_10.jpg" width="600px" height="300px">
</div>

---

### توضیحات شماتیک مدار ✒️

<ol>
<li>
اتصالات LCD
<ul>
<li>پایه های 1 و 16 به Gnd</li>
<li>پایه های 2 و 15 به Vcc</li>
<li>پایه 3 به پایه وسط پتانسیومتر</li>
<li>پایه 4 ( rs ) به پین 12 آردوینو</li>
<li>پایه 5 به Gnd</li>
<li>پایه 6 ( en ) به پین 11 آردوینو</li>
<li>پایه های 11 تا 14 ( data ) به پین های 7 تا 4 آردوینو</li>
</ul>
</li>
<li>
اتصالات پتانسیومتر
<ul>
<li>پایه های طرفین یکی به Gnd و دیگری به Vcc</li>
<li>پایه وسطی به پایه 3 LCD</li>
</ul>
</li>
<li>
اتصالات اولتراسونیک
<ul>
<li>پایه 1 به Vcc</li>
<li>پایه 2 ( trig ) به پین 10 آردوینو</li>
<li>پایه 3 ( echo ) به پین 9 آردوینو</li>
<li>پایه 4 به Gnd</li>
</ul>
</li>
</ol>

---

### نتیجه گیری 👀

ماژول اولتراسونیک یک ماژول قدرتمند با کاربردهای فراوانی می باشد که با استفاده از آن می توان انواعی از تجهیزات مختلف را پیاده سازی کرد. از مشکلات این ماژول نیز می توان به محدود بودن دقت در حد سانتی متر (و نه کمتر) و همچنین محدود بودن زاویه ارسال و دریافت سیگنال که فقط در یک جهت می باشد اشاره کرد.
