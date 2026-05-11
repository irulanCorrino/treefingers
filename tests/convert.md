### convert
```
#convert to binary --irulanCorrino
learn widthBits $value, $iterator {
     $check = 0
     while ($check < $value) {
          $iterator = $iterator + 1
          $check = 2 ^ $iterator
          }
     if $check > $value {
        $check = $check - 1
        if $check >= $value { $iterator = $iterator - 1 }
        }
     return $iterator + 1
     }
learn wrapperSR $value, $address, $dLength {
     if $value {
      $firstOperand = shiftRightExplicit $value, $address
      $addressShifted = $address + $dLength
      $secondOperand = shiftRightExplicit $value, $addressShifted
      $result = $firstOperand - $secondOperand * (2 ^ $dLength)
      return $result
      }
      else { return $value }
     }
learn shiftRightExplicit $value, $address {
     $c = $value
     repeat $address {
           $oddity = mod $c, 2
           if not $oddity { $c = $c / 2 }
            else { $c = ($c - 1) / 2 }
           }
     return $c
     }
$answer = true
while $answer {
     $variable = ask "input a number or say 'quit'"
     if $variable == "quit" or $variable =="QUIT" { $answer = false }
      else {
        reset
        spritehide#comment it out to have some fun
        penup
        pencolor 255, 0, 0
        $variableWidth = widthBits $variable, 0
        direction 270
        forward 5*$variableWidth
        direction 0
        pencolor 0, 255, 0
        print $variableWidth
        forward 12
        pencolor 255, 0, 0
        print "the width is "
        forward 12
        pencolor 0, 0, 255
        for $addr = $variableWidth - 1 to 0 step -1 {
            direction 0
            print wrapperSR $variable, $addr, 1
            direction 90
            forward 10
            }
        backward 10*$variableWidth
        direction 0
        forward 12
        pencolor 0, 0, 255
        print "in binary is"
        forward 12
        pencolor 255, 127, 255
        print "a number " + $variable
        }
     }
exit
#
```
<img width="533" height="533" title="convert to binary" src="https://github.com/user-attachments/assets/38d25b6a-f103-42ec-bba3-5435f60a5496" />

### unwrap
```
#convert to binary & unwrap as 2-bit granular bitfield --irulanCorrino
learn widthBits $value, $iterator {
     $check = 0
     while ($check < $value) {
          $iterator = $iterator + 1
          $check = 2 ^ $iterator
          }
     if $check > $value {
        $check = $check - 1
        if $check >= $value { $iterator = $iterator - 1 }
        }
     return $iterator + 1
     }
learn wrapperSR $value, $address, $dLength {
     if $value {
      $firstOperand = shiftRightExplicit $value, $address
      $addressShifted = $address + $dLength
      $secondOperand = shiftRightExplicit $value, $addressShifted
      $result = $firstOperand - $secondOperand * (2 ^ $dLength)
      return $result
      }
      else { return $value }
     }
learn shiftRightExplicit $value, $address {
     $c = $value
     repeat $address {
           $oddity = mod $c, 2
           if not $oddity { $c = $c / 2 }
            else { $c = ($c - 1) / 2 }
           }
     return $c
     }
$answer = true
while $answer {
     $variable = ask "input a number or say 'quit'"
     if $variable == "quit" or $variable =="QUIT" { $answer = false }
      else {
        reset
        spritehide#comment it out to have some fun
        penup
        pencolor 255, 0, 0
        $variableWidth = widthBits $variable, 0
        direction 270
        forward 5*$variableWidth
        direction 0
        pencolor 0, 255, 0
        print $variableWidth
        forward 12
        pencolor 255, 0, 0
        print "the width is "
        forward 12
        pencolor 0, 0, 255
        for $addr = $variableWidth - 1 to 0 step -1 {
            direction 0
            print wrapperSR $variable, $addr, 1
            direction 90
            forward 10
            }
        backward 10*$variableWidth
        direction 0
        forward 12
        pencolor 0, 255, 255
        for $addr = $variableWidth - 2 to 0 step -2 {
            direction 0
            print wrapperSR $variable, $addr, 2
            direction 90
            forward 20
            }
        backward 10*$variableWidth
        direction 0
        forward 12
        pencolor 0, 0, 255
        print "in binary is"
        forward 12
        pencolor 255, 127, 255
        print "a number " + $variable
        }
     }
exit
#
```
<img width="533" height="533" title="unwrap bitfield" src="https://github.com/user-attachments/assets/06753d20-2274-45e8-b111-90714506db37" />

### wrap
```
#convert to binary & unwrap as 2-bit granular bitfield $ wrap back to decimal --irulanCorrino
learn widthBits $value, $iterator {
     $check = 0
     while ($check < $value) {
          $iterator = $iterator + 1
          $check = 2 ^ $iterator
          }
     if $check > $value {
        $check = $check - 1
        if $check >= $value { $iterator = $iterator - 1 }
        }
     return $iterator + 1
     }
learn wrapperSR $value, $address, $dLength {
     if $value {
      $firstOperand = shiftRightExplicit $value, $address
      $addressShifted = $address + $dLength
      $secondOperand = shiftRightExplicit $value, $addressShifted
      $result = $firstOperand - $secondOperand * (2 ^ $dLength)
      return $result
      }
      else { return $value }
     }
learn shiftRightExplicit $value, $address {
     $c = $value
     repeat $address {
           $oddity = mod $c, 2
           if not $oddity { $c = $c / 2 }
            else { $c = ($c - 1) / 2 }
           }
     return $c
     }
#
learn shiftLeftExplicit $value, $address {
     $d = $value
     repeat $address {
           $d = $d * 2
           }
     return $d
     }
learn packBits $value, $input, $address {
     return $value + shiftLeftExplicit $input, $address
     }
#
$answer = true
while $answer {
     $variable = ask "input a number or say 'quit'"
     if $variable == "quit" or $variable =="QUIT" { $answer = false }
      else {
        reset
        spritehide#comment it out to have some fun
        $copy = 0
        penup
        pencolor 255, 0, 0
        $variableWidth = widthBits $variable, 0
        direction 270
        forward 5*$variableWidth
        direction 0
        pencolor 0, 255, 0
        print $variableWidth
        forward 12
        pencolor 255, 0, 0
        print "the width is "
        forward 12
        pencolor 0, 0, 255
        for $addr = $variableWidth - 1 to 0 step -1 {
            direction 0
            print wrapperSR $variable, $addr, 1
            direction 90
            forward 10
            }
        backward 10*$variableWidth
        direction 0
        forward 12
        pencolor 0, 255, 255
        for $addr = $variableWidth - 2 to 0 step -2 {
            direction 0
            $field = wrapperSR $variable, $addr, 2
            print $field
            $copy = packBits $copy, $field, $addr
            direction 90
            forward 20
            }
        backward 10*$variableWidth
        direction 0
        forward 12
        pencolor 0, 0, 255
        print "in binary are"
        forward 12
        pencolor 255, 127, 64
        print "and its copy " + $copy
        forward 12
        pencolor 255, 127, 255
        print "a number " + $variable
        }
     }
exit
#
```
<img width="533" height="533" title="wrap bitfield" src="https://github.com/irulanCorrino/treefingers/blob/main/wrapbitfield.svg" />
