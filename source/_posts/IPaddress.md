title: 用Python获取外网IP并提交到花生壳，邮件通知
date: 2015-10-14 20:12:17
categories: Python
tags:
---
``` python
#-*- coding:utf-8 -*-
import urllib
import re
import time
import datetime

IPadd=""
username="x715067069"
password="******"
hostname="x715067069.eicp.net"

url =["http://ddns.oray.com/checkip","http://www.whereismyip.com/","http://ip.qq.com/"]
while True:
	with open('addstr.txt', 'r+') as f:
		IPadd=f.read()
		print "The last IP address is:",IPadd
	#print url
	try:
		request = urllib.urlopen(url[0]).read()
	except:
		try:
			request = urllib.urlopen(url[1]).read()
		except:
			try:
				request = urllib.urlopen(url[2]).read()
			except:
				print("Please check your network !")
				
	theIP = re.findall(r"\d{1,3}\.\d{1,3}\.\d{1,3}.\d{1,3}",request)
	print "Your IP address is:" ,theIP[0]
	if theIP[0]==IPadd :
		print("IP address not change !")
	else:
		with open('addstr.txt', 'w') as f:
			f.write(theIP[0])
		with open('IPhistory.txt','a') as f:
			dt = datetime.datetime.now()
			f.write(theIP[0]+'\t'+dt.strftime('%Y-%m-%d %I:%M:%S %p')+'\n')
		urlo1=("http://"+username+":"+password+"@ddns.oray.com/ph/update?hostname="+hostname+"&"+theIP[0])
		req=urllib.urlopen(urlo1).read()]
		print (req)
	print("*********************")
	time.sleep(60*10)
#http://username:password@ddns.oray.com/ph/update?hostname=yourhostname&myip=ipaddress

```