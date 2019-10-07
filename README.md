### **TASK 1:**
In the document below, Net Amount/Gross Amount information is printed on a grey
background. We need to clean such documents, in such a way that the grey background
is removed and the textual information like the amount and text “Net Pay”/”Gross Pay”
etc. are visible clearly.

### **CODE:**

```
#include "pch.h"
#include <iostream>
#include "opencv2/imgproc.hpp"
#include "opencv2/imgcodecs.hpp"
#include "opencv2/highgui.hpp"
using namespace std;
using namespace cv;


int main(int argc, char ** argv)
{
	Mat lines, dif, im, dst = imread("C:/Users/ASus/Desktop/CodingTest-Samples/000004.tif");

	medianBlur(dst, im, 3);
	GaussianBlur(im, im, Size(7, 7), 1);
	threshold(im, im, 90, 255, THRESH_BINARY);
	GaussianBlur(im, im, Size(1, 1), 0);


	imwrite("C:/Users/ASus/Desktop/CodingTest-Samples/0000044.tif", im);
	
	return 0;
}

````


### **BEFORE**

![000004](https://user-images.githubusercontent.com/29340078/66316127-c29f7980-e91f-11e9-87fb-046e70ebd726.jpg)

### **AFTER**

![0000044](https://user-images.githubusercontent.com/29340078/66316274-0f835000-e920-11e9-886f-180b1d09b2f8.jpg)

----------------------------------------------------------------------------------------------------------

### **BEFORE**

![000001](https://user-images.githubusercontent.com/29340078/66316129-c3381000-e91f-11e9-891a-132316157c6a.jpg)

### **AFTER**

![0000011](https://user-images.githubusercontent.com/29340078/66316221-f084be00-e91f-11e9-85f2-2eea7b94f000.jpg)
----------------------------------------------------------------------------------------------------------
### **BEFORE**

![000003](https://user-images.githubusercontent.com/29340078/66316132-c3d0a680-e91f-11e9-80cc-2d4524ed0e80.jpg)

### **AFTER**
![0000033](https://user-images.githubusercontent.com/29340078/66316262-08f4d880-e920-11e9-9840-92054e2c8312.jpg)



### **TASK 2:**
In document below, the textual information is present in the gray colored or light colored
font. We need to clean such documents, in such a way that the grey background is
removed and all the textual information like the texts “BORROWER
NAME”/”BERNARDO PIZZARO” etc. are visible clearly


### **CODE:**

```
#include "pch.h"
#include <iostream>
#include "opencv2/imgproc.hpp"
#include "opencv2/imgcodecs.hpp"
#include "opencv2/highgui.hpp"
using namespace std;
using namespace cv;

int dilation_size = 0;
int dilation_type = MORPH_CROSS;

int main(int argc, char ** argv)
{
	Mat kernel, lines, dif, im = imread("C:/Users/ASus/Desktop/CodingTest-Samples/2.tif");
	
	threshold(im, im, 205, 255, THRESH_BINARY);
	
	//medianBlur(im, im, 3);

	Mat element = getStructuringElement(dilation_type,
		Size(2 * dilation_size + 1, 2 * dilation_size + 1),
		Point(dilation_size, dilation_size));
	/// Apply the dilation operation
	dilate(im, im, element);
	
	imwrite("C:/Users/ASus/Desktop/CodingTest-Samples/02.tif", im);
	
	return 0;
}

```
### **BEFORE**

![000002](https://user-images.githubusercontent.com/29340078/66316708-db5c5f00-e920-11e9-8186-3051c517e8a6.jpg)

### **AFTER**

![01](https://user-images.githubusercontent.com/29340078/66318438-fc727f00-e923-11e9-8450-f88bf9d1d438.jpg)

----------------------------------------------------------------------------------------------------------

### **BEFORE**

![000005](https://user-images.githubusercontent.com/29340078/66316800-fc24b480-e920-11e9-880d-f869c3441462.jpg)

### **AFTER**

![02](https://user-images.githubusercontent.com/29340078/66318446-00060600-e924-11e9-8113-570ab269457a.jpg)
