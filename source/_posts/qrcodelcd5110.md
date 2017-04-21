title: 生成QR显示到nokia LCD_5110
date: 2015-10-21 20:34:27
categories:
- Python
tags:
- QRcode
- Python
- PIL
- 树莓派
---
### 用纸盒给树莓派做了个新家，装上了「显示器」
![](http://7xnf9d.com1.z0.glb.clouddn.com/IMG_20151021_200513.jpg)
![](http://7xnf9d.com1.z0.glb.clouddn.com/IMG_20151021_200352.jpg)
![](http://7xnf9d.com1.z0.glb.clouddn.com/IMG_20151021_200541.jpg)

### 最近好烦，不想记录过程了代码↓↓↓
``` python
#coding=utf-8
#这些不用管
import time
import Adafruit_Nokia_LCD as LCD
import Adafruit_GPIO.SPI as SPI
import Image
import ImageDraw
import ImageFont
import qrcode

DC = 23
RST = 24
SPI_PORT = 0
SPI_DEVICE = 0
disp = LCD.PCD8544(DC, RST, spi=SPI.SpiDev(SPI_PORT, SPI_DEVICE, max_speed_hz=4000000))
disp.begin(contrast=60)
disp.clear()
disp.display()

qr = qrcode.QRCode(     
    version=1,     #值为1~40的整数，控制二维码的大小（最小值是1，是个12×12的矩阵）。 如果想让程序自动确定，将值设置为 None 并使用 fit 参数即可。
    error_correction=qrcode.constants.ERROR_CORRECT_L,    									 #控制二维码的错误纠正功能。可取值下列4个常量。
    box_size=4,     #控制二维码中每个小格子包含的像素数。										#ERROR_CORRECT_L：大约7%或更少的错误能被纠正。
    border=0, 	#控制边框（二维码与图片边界的距离）包含的格子数（默认为4，是相关标准规定的最小值）		#ERROR_CORRECT_M（默认）：大约15%或更少的错误能被纠正。
) 																								#ROR_CORRECT_H：大约30%或更少的错误能被纠正。
qr.add_data(u'http://raspi.picp.net') 
qr.make(fit=True)  
img1 = qr.make_image()
#img.save('qr.png')

img=Image.open("blank.png")
img.paste(img1.resize((48,48)),(36,0))#将img1粘贴到img的18,0处
img.save("out.png")

image = Image.open('out.png').resize((LCD.LCDWIDTH, LCD.LCDHEIGHT), Image.ANTIALIAS).convert('1')

font = ImageFont.truetype('/home/pi/Desktop/pi/5110/font/Minecraftia-Regular.ttf', 8)
fontc = ImageFont.truetype('/usr/share/fonts/truetype/wqy/wqy-microhei.ttc', 12)
draw = ImageDraw.Draw(image)
draw.text((0,0), u'卓大师', font=fontc)
draw.text((0,11), u'的树莓', font=fontc)
draw.text((0,23), u'派小站', font=fontc)
draw.text((0,35), u'→_→', font=fontc)
#输出
disp.image(image)
disp.display()
```