```
learn f {# global variables (from "Effective C" by Robert Seacord, chapter "Order of evaluation")
     return $glob + 10
}
learn g {
     $glob = 42
     return $glob
     }
learn max {
     if (f) > (g) { return true }
      else { return false }
     }
# main
reset
canvassize 750, 800
spritehide
go 600, 400
pu
repeat 18 {
      $glob = 0
      repeat 10 {
            fw 40
            if max { print "-" }
             else { print "*" }
            bw 40
            turnleft 2
            fw 8
            }
      }
# kTurtle has predictable order of execution
```
![order of execution](https://github.com/user-attachments/assets/84e45a69-3033-4cac-a914-44b91d10c4c3)
