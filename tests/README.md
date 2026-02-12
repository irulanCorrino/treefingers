## tests
i will keep tests at this directory
#### a code (global variables)
```
learn wall $wall {#a test by irulan (global variables)
     pencolor 40, 255, 127
     $wall = "Hello, wall!"
     print $wall
     fw 20
     pencolor 255, 40, 127
     }
learn fence {
     pencolor 255, 40, 255
     $wall = "Hello, fence!"
     print $wall
     fw 20
     pencolor 127, 40, 127
     }
learn fridge0 {
     wall $wall
     print $wall + " fridge*0"
     }
learn fridge1 {
     fence
     print $wall + " fridge*1"
     }
reset
spritehide
canvassize 400, 600
go 100, 550
$i = 2
while $i {
     $i = $i - 1
     $wall = "nobody"
     if $i { wall $wall }
      else { fence }
     $wall = "nobody"
     if $i { fence }
      else { wall $wall }
     fw 40
     print $wall
     fw 40
     $wall = "nobody"
     fridge0
     fw 20
     print $wall
     $wall = "nobody"
     pu
     forward 40
     pd
     fridge1
     fw 20
     print $wall
     pu
     forward 20
     pd
     turnright 90
     forward 150
     pu
     backward 150
     turnleft 90
     forward 20
     pd
     }

```
#### a picture
![wall](https://github.com/user-attachments/assets/ccfd6415-a379-4972-99fd-c919790e516d)
