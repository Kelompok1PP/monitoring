# monitoring
def monitoring ():
	import psutil 
	from time import sleep

	processor = psutil.cpu_percent()
	mem = psutil.virtual_memory().percent

	rx = psutil.net_io_counters().bytes_sent
	tx = psutil.net_io_counters().bytes_recv

	sleep(1)
	rx_1= psutil.net_io_counters().bytes_sent
	tx_1= psutil.net_io_counters().bytes_recv
	rx = operasi (rx, rx_1)
	tx = operasi (tx, tx_1)

	print ('''
		System Monitoring 
		CPU 	: {}%
		Memory	: {}%
		TX/RX	: {} Kbps/ {} Kbps

	      '''.format(processor, mem, rx, tx))

def operasi (old, new):
	new = new - old 
	new = (new * 8) / 1000
	return new

def monitor():
	from time import sleep
	while(True):
		monitoring()
		sleep(5)

try:
	monitor()
except:
	print(" \n\t Selesai.")
