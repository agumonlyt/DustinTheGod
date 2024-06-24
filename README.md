# DustinTheGod
Thank You Dustin You Are The Best

https://github.com/qlvbrknp/maple-bot

tldr; i was trying to recreate what Dustin wrote there for his gdi_capture.dll
i failed to replicate his work no matter how i try i always end up with slow screen capturing speed. 
but today, a very kind user helped me assembly the .dll and showed me the function. 
i was surprised. Dustin was using createdibsection. 

before this i was using selectobject, bitblt, then getbitmapbits, 

some drawing: 

my work/experiments:

GetDC --> CreateCompatibleDC --> CreateCompatibleBitmap --> 
SelectObject --> BitBlt --> GetBitmapBits

however this is slow, the GetBitmapBits step will take another .0004 seconds to copy over to the buffer pointer. 
and i was also trying to retrive the Bitmap from HBITMAP. But it doesn't work that way. 

now the new method (Dustin's work) is like this:

GetDC --> CreateDIBSection --> CreateCompatibleDC --> 
SelectObject --> BitBlt

so CreateDIBSection step actually somehow directly copied the pixel to the buffer without extra step using GetBitmapBits. 





now the average frame took .0014 second to .0023 second. 

NOW, question: can it be even faster?

like how to compile the .dll

or omit some variable initialization

maybe direct3d?