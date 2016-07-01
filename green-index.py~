import cv2
import numpy as np

def getco(event,x,y,flags,param):
	if event == cv2.EVENT_LBUTTONDBLCLK: 
		print(res[y][x],y,x)
file_name = raw_input("Enter the file name\n")
image = cv2.imread(file_name)
#rows,columns,channel = image.size
print(image.shape[0])
height = image.shape[0]
width = image.shape[1]
count=0
for i in range(0,height):
	for j in range(0,width):
		if(image[i][j][0] in range(30,60) and image[i][j][1] in range(30,60) and image[i][j][2] in range(30,60)):
			image[i][j]=(255,255,255)
			count=count+1	

kernel = np.ones((5,5),np.uint8)
cv2.imshow("one",image)
closing = cv2.morphologyEx(image, cv2.MORPH_CLOSE, kernel)  #blurring
cv2.imwrite("output_notgreen.jpg",closing)
cv2.imshow("second",closing)
image = cv2.imread(file_name)
closed = cv2.imread("output_notgreen.jpg",0)
#cv2.imshow("image",closed)
cv2.setMouseCallback('image',getco)
ret, mask = cv2.threshold(closed, 254, 255, cv2.THRESH_BINARY)
res=cv2.bitwise_and(image,image,mask = mask)
cv2.imshow("mask",res)
cv2.imwrite("ouput_green.jpeg",res)

cv2.waitKey(0)


