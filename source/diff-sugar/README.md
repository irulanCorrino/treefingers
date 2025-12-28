###### this is an entry for diff sugar --so you would may be able to see diffs between versions placed into different folders [i cannot use branching as of yet so i use separate folders for versions that have big number bumps]

```
#treefingers 2.0.2  digital calligraphy application for runic script [elder futhark]
#    Copyright (C) 2014-2022  irulanCorrino
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.
#____________________________________________________________________________
#
# thonri oyer empty_by_irulan_corrino_ --a field, an action (probably interface base)
##_fractal_dimension
## _makes_series_--a_divide_to_b_is_sqrt_of_2_
learn size2 $a {
      $n = $a / sqrt 2
      return $n
      }
#
learn size $a, $n {
      $n = $a / sqrt 2
      }
#
learn line $base, $iteration {
      $stepLenght = 4 * $base / $iteration
      return $stepLenght
      }
#
learn shiftRight $value, $power {
      $c = 1
      $d = $value
      while $d > 2 {
           $c = $c + 1
           $d = $d / 2
           }
      $power = $c
      }
#
learn iIterator $base, $fixBitIterator, $iteration, $x, $y, $runOnce {
#_a_field_(an_empty_rune)_--common_case_
      go $x, $y
      $markOfThirdStemX = 0
      $markOfThirdStemY = 0
      $stepLenght = 0
      if $runOnce { $iteration = $iteration * 2 }
      penup
      $stepLenght = line $base, $iteration
      forward $stepLenght
      $mOfSecondStemX = getx
      $mOfSecondStemY = gety
      turnleft 60
      pendown
      if not $runOnce { $runOnce = true }
      lips $stepLenght, $markOfThirdStemX, $markOfThirdStemY, $mOfSecondStemX, $mOfSecondStemY, $x, $y, $runOnce, $base, $fixBitIterator, $iteration
      }
#
learn fieldEntry $stepLenght, $markOfThirdStemX, $markOfThirdStemY, $mOfSecondStemX, $mOfSecondStemY, $x, $y, $runOnce, $base, $fixBitIterator, $iteration, $entry {
      if $entry == 1 { iIterator $base, $fixBitIterator, $iteration, $x, $y, $runOnce }
        else {
          if $entry == 2 { iIterator $base, $fixBitIterator, $iteration, $mOfSecondStemX, $mOfSecondStemY, $runOnce }
           else { iIterator $base, $fixBitIterator, $iteration, $markOfThirdStemX, $markOfThirdStemY, $runOnce }
             }
          }
      }
#
learn lips $stepLenght, $markOfThirdStemX, $markOfThirdStemY, $mOfSecondStemX, $mOfSecondStemY, $x, $y, $runOnce, $base, $fixBitIterator, $iteration {
       $entry = 0
       $f = 0
       repeat 3 {
            $f = $f + 1
            forward $stepLenght
            if $f == 2 { 
               $markOfThirdStemX = getx
               $markOfThirdStemY = gety
               }
            turnleft 120
            }
       turnleft 300
       if $iteration != $fixBitIterator {
          repeat 3 {
               $entry = $entry + 1
               fieldEntry $stepLenght, $markOfThirdStemX, $markOfThirdStemY, $mOfSecondStemX, $mOfSecondStemY, $x, $y, $runOnce, $base, $fixBitIterator, $iteration, $entry
               }
         }
      }
#
learn container $sheetB, $fixBits, $wirPointerX, $wirPointerY {
      $fixBitIterator = $fixBits * 2
      $base = $sheetB
      $iteration = 2
      $runOnce = false
      iIterator $base, $fixBitIterator, $iteration, $wirPointerX, $wirPointerY, $runOnce
      }
# thonri oyer empty
#
#_i(h)waz
#_--a_compiler_namespace_
# pronunciation_--
# gethenian: iywa terrain: ihwar i(h)waz ei(h)waz
learn ihwaz $zoomValue, $appearance {
    if not $appearance {
     $a1 = mirrorIt 15
     $a2 = mirrorIt 165
     $a3 = mirrorIt 199
     }
     else {
       $a1 = 15
       $a2 = 165
       $a3 = 199
       }
    $l1 = 10 * $zoomValue
    $l2 = 40 * $zoomValue
    penup
    forward 32 * $zoomValue
    if $appearance {
     turnleft 270
     forward 10 * $zoomValue
     turnleft 90
     }
     else {
       turnleft 90
       forward 8 * $zoomValue
       turnleft 270
       }
    pendown
    $l3 = 12 * $zoomValue
    turnleft $a1
    forward $l1
    turnleft $a2
    forward $l2
    turnleft $a3
    forward $l3     
    }
# iywa ihwar i(h)waz ei(h)waz
#
#_berkanan
# pronunciation_--
# gethenian: bessa terrain: bercana berkanan
learn berkanan $zoomValue, $appearance {
    if not $appearance {
     $a1 = mirrorIt 21
     $a2 = mirrorIt 69
     $a3 = mirrorIt 111
     $a4 = mirrorIt 107
     }
     else {
       $a1 = 21
       $a2 = 69
       $a3 = 111
       $a4 = 107
       }
    $l1 = 40 * $zoomValue
    penup
    forward $l1
    if $appearance {
     turnleft 270
     forward 5 * $zoomValue
     turnleft 90
     }
     else {
       turnleft 90
       forward 2 * $zoomValue
       turnleft 270
       }
    pendown
    $l2 = 12 * $zoomValue
    $l3 = 5 * $zoomValue
    $l4 = 9 * $zoomValue
    turnleft 180
    forward $l1
    penup
    backward $l1
    pendown
    turnleft $a1
    forward $l2
    turnright $a2
    forward $l3
    turnleft $a3
    forward $l4
    turnright $a4
    forward $l2
    }
# bessa bercana berkanan
#
#_gebo
#_--possibly_a_compiler_
# pronunciation_--
# gethenian: gad terrain: gedo gebo
learn gebo $zoomValue {
    penup
    forward 38 * $zoomValue
    turnleft 90
    forward 10 * $zoomValue
    turnleft 270
    pendown
    $l1 = 48 * $zoomValue
    $l2 = 37 * $zoomValue
    $l3 = 52 * $zoomValue
    turnright 134
    forward $l1
    penup
    turnleft 144
    forward $l2
    pendown
    turnleft 130
    forward $l3
    }
# gad gedo gebo
#
#_tiwaz
# pronunciation_--
# gethenian: chawa terrain: teiwaz tiwaz
learn tiwaz $zoomValue {
    $l1 = 40 * $zoomValue
    penup
    forward $l1
    turnleft 270
    forward 7 * $zoomValue
    turnleft 90
    pendown
    $l2 = 10 * $zoomValue
    $l3 = 12 * $zoomValue
    turnleft 180
    forward $l1
    penup
    backward $l1
    pendown
    turnleft 19
    forward $l2
    penup
    backward $l2
    pendown
    turnright 40
    forward $l3
    }
# chawa teiwaz tiwaz
#
#_mannaz
#_--possibly_a_compiler_
# pronunciation_--
# gethenian: mand terrain: mannaz
learn mannaz $zoomValue {
    $l1 = 40 * $zoomValue
    penup
    forward $l1
    turnleft 270
    forward 19 * $zoomValue
    turnleft 90
    pendown
    $l2 = 44 * $zoomValue
    $l3 = 32 * $zoomValue
    $l4 = 50 * $zoomValue
    $l5 = 35 * $zoomValue
    $l6 = 16 * $zoomValue
    turnleft 180
    forward $l1
    penup
    turnleft 225
    forward $l2
    turnleft 135
    pendown
    forward $l3
    turnleft 142
    penup
    forward $l4
    pendown
    turnleft 160
    forward $l5
    penup
    turnleft 237
    forward $l6
    pendown
    turnright 118
    forward $l3
    }
# mand mannaz
#
#_othila _--mirror_
#_a_compiler_
learn placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance {
    rememberIt $xPoint, $yPoint
    $lA = 57
    $lB = size2 $lA
    $lA = $lA * $zoomValue
    $lB = $lB * $zoomValue
    $spacing =(sqrt ( ($lA ^ 2) + ($lB ^ 2) ))
    switchMode $latitudeView, $fork, $spacing, $zoomValue
    if $system {
       setColor 3
       forward $lA
       turnleft 90
       forward $lB
       turnleft 90
       forward $lA
       turnleft 90
       forward $lB
       setColor 1
       }
    penup
    if not $system { turnleft 90 }
     else { turnleft 180 }
    forward $lB / 2
    if $appearance { forward $lB / 8}
     else { backward $lB / 8}
    turnleft 270
    forward $lA / 8
    pendown
    if not $cluster { $latitudeView  = false }
    }
learn mirrorIt $value {
    $angle = 360 - $value
    return $angle
    }
learn rememberIt $xPoint, $yPoint {
    $xPoint = getx
    $yPoint = gety
    }
# pronunciation_--
# gethenian: othir terrain: othala othila
learn othila $zoomValue {
    $a1 = 31
    $a2 = 65
    $a3 = 117
    $a4 = 78
    $l1 = 28 * $zoomValue
    $l2 = 28 * $zoomValue
    $l3 = 19 * $zoomValue
    $l4 = 45 * $zoomValue
    turnright $a1
    forward $l1
    turnleft $a2
    forward $l2
    turnleft $a3
    forward $l3
    turnleft $a4
    forward $l4
    }
# othir othala othila
#
#_naudiz
# pronunciation_--
# gethenian: naue terrain: naupir naudiz
learn naudiz $zoomValue, $appearance {
    if not $appearance {
     $a1 = mirrorIt 170
     $a2 = mirrorIt 67
     }
     else {
       $a1 = 170
       $a2 = 67
       }
    $l1 = 43 * $zoomValue
    penup
    forward $l1
    if $appearance {
     turnleft 270
     forward 8 * $zoomValue
     turnleft 90
     }
     else {
     turnleft 90
     forward 12 * $zoomValue
     turnleft 270
       }
    pendown
    $l2 = 29 * $zoomValue
    $l3 = 31 * $zoomValue
    turnleft 180
    forward $l1
    turnleft $a1
    penup
    forward $l2
    turnleft $a2
    pendown
    forward $l3
    }
# naue naupir naudiz
#
#_algiz
#--_possibly_a_compiler_
# pronunciation_--
# gethenian: argir terrain: algir algiz
learn algiz $zoomValue {
    $l1 = 42 * $zoomValue
    penup
    forward $l1
    turnleft 270
    forward 6 * $zoomValue
    turnleft 90
    pendown
    $l2 = 41 * $zoomValue
    $l3 = 18 * $zoomValue
    turnleft 180
    forward $l1
    penup
    turnleft 190
    forward $l2
    pendown
    turnright 167
    forward $l3
    turnleft 115
    forward $l3
    }
learn cryptic $crypticValue, $defaultZoom {
    if not $crypticValue {
     return $defaultZoom / 3
     }
     else {
       if $crypticValue == 1 {
        return $defaultZoom
        }
        else {
          if $crypticValue == 2 {
           return 2 * size2 cryptic 0, $defaultZoom
           }
           else {
             if $crypticValue == 3 {
              return $defaultZoom / 5
              }
              else {
                if $crypticValue == 4 {
                 return  cryptic 2, $defaultZoom / 5
                 }
                }
             }
          }
       }
    }
learn time $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance {
    go $xPoint, $yPoint
    $lA = 46 * cryptic 2, $zoomValue
    $lB = size2 $lA
    placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
    forward 10* $zoomValue
    turnleft 90
    forward 5* $zoomValue
    turnright 90
    iPenErase 2 * $lB * cryptic 2, $zoomValue
    forward $lA
    iPenMark $zoomValue
#fontsize 40
#print $lB
#forward 60
#print $lA
#dbg&tuning
    }
# argir algir algiz
#
#_thurisaz
# pronunciation_--
# gethenian: thured terrain: thurisaz
learn thurisaz $zoomValue {
    $l1 = 43 * $zoomValue
    penup
    forward $l1
    turnleft 270
    forward $zoomValue
    turnleft 90
    pendown
    $l2 = 41 * $zoomValue
    $l3 = 26 * $zoomValue
    $l4 = 28 * $zoomValue
    turnleft 180
    forward $l1
    penup
    backward $l2
    pendown
    turnleft 38
    forward $l3
    turnleft 285
    forward $l4
    }
# thured thurisaz
#
#_uruz
# pronunciation_--
# gethenian: uru terrain: uruz
learn uruz $zoomValue, $appearance {
    if not $appearance {
     $a1 = mirrorIt 5
     $a2 = mirrorIt 40
     $a3 = mirrorIt 130
     }
     else {
       $a1 = 5
       $a2 = 40
       $a3 = 130
       }
    if $appearance {
     penup
     turnleft 90
     forward 5 * $zoomValue
     turnleft 270
     pendown
     }
     else {
     penup
     turnleft 270
     forward 5 * $zoomValue
     turnleft 90
     pendown
       }
    $l1 = 28 * $zoomValue
    $l2 = 20 * $zoomValue
    $l3 = 42 * $zoomValue
    turnright $a1
    forward $l1
    turnright $a2
    forward $l2
    turnright $a3
    forward $l3
    }
# uru uruz
#
#_ingwaz 
#_--possibly_is_a_compiler_
# pronunciation_--
# gethenian: ingif terrain: ingwar ingwaz
learn ingwaz $zoomValue {
    $l1 = 25 * $zoomValue
    penup
    forward 41 * $zoomValue
    turnleft 90
    forward 8 * $zoomValue
    turnleft 270
    pendown
    $l2 = 28 * $zoomValue
    $l3 = 45 * $zoomValue
    turnright 140
    forward $l1
    turnright 75
    forward $l2
    penup
    turnright 165
    forward $l3
    pendown
    turnleft 175
    forward $l1
    turnleft 77
    forward $l2
    }
# ingif ingwar ingwaz
#
#_isaz
# pronunciation_--
# gethenian: isa terrain: isa isaz
learn isaz $zoomValue {
    $l1 = 42 * $zoomValue
    penup
    forward $l1
    turnleft 270
    forward 5 * $zoomValue
    turnleft 90
    pendown
    turnleft 180
    forward $l1
    }
# isa isaz
#
#_dagaz
#_--possibly_a_compiler
# pronunciation_--
# gethenian: dawa terrain: dagaz
learn dagaz $zoomValue {
    $l1 = 42 * $zoomValue
    penup
    forward $l1
    turnleft 90
    forward 8 * $zoomValue
    turnleft 270
    pendown
    $l2 = 47 * $zoomValue
    $l3 = 40 * $zoomValue
    $l4 = 45 * $zoomValue
    turnleft 180
    forward $l1
    turnleft 148
    forward $l2
    turnright 148
    forward $l3
    turnright 148
    forward $l4
    }
# dawa dagaz
#
#_wunjo
# pronunciation_--
# gethenian: wunyo terrain: wunjo
learn wunjo $zoomValue, $appearance {
    if not $appearance {
     $a1 = mirrorIt 223
     $a2 = mirrorIt 263
     }
     else {
       $a1 = 223
       $a2 = 263
       }
    $l1 = 43 * $zoomValue
    penup
    forward $l1
    pendown
    $l2 = 41 * $zoomValue
    $l3 = 18 * $zoomValue
    $l4 = 16 * $zoomValue
    turnleft 180
    forward $l1
    penup
    turnleft 180
    forward $l2
    pendown
    turnleft $a1
    forward $l3
    turnleft $a2
    forward $l4
    }
# wunyo wunjo
#
#_raido
# pronunciation_--
# gethenian: reith terrain: raido raidho
learn raido $zoomValue, $appearance {
    if not $appearance {
     $a1 = mirrorIt 221
     $a2 = mirrorIt 265
     $a3 = mirrorIt 95
     }
     else {
       $a1 = 221
       $a2 = 265
       $a3 = 95
       }
    $l1 = 44 * $zoomValue
    penup
    forward $l1
    pendown
    $l2 = 42 * $zoomValue
    $l3 = 14 * $zoomValue
    $l4 = 12 * $zoomValue
    $l5 = 30 * $zoomValue
    turnleft 180
    forward $l1
    penup
    turnleft 180
    forward $l2
    pendown
    turnleft $a1
    forward $l3
    turnleft $a2
    forward $l4
    turnleft $a3
    forward $l5
    }
# reith raido raidho
#
#_fehu
# pronunciation_--
# gethenian: fehu terrain: fehu
learn fehu $zoomValue, $appearance {
    if not $appearance {
     $a1 = mirrorIt 162
     $a2 = mirrorIt 168
     $a3 = mirrorIt 190
     }
     else {
       $a1 = 162
       $a2 = 168
       $a3 = 190
       }
    $l1 = 41 * $zoomValue
    penup
    forward $l1
    pendown
    $l2 = 46 * $zoomValue
    $l3 = 23 * $zoomValue
    $l4 = 21 * $zoomValue
    $l5 = 26 * $zoomValue
    turnleft 180
    forward $l1
    penup
    turnleft $a1
    forward $l2
    pendown
    turnleft $a1
    forward $l3
    penup
    turnleft $a2
    forward $l4
    pendown
    turnleft $a3
    forward $l5
    }
learn switchMode $latitudeView, $fork, $spacing, $zoomValue {#
    if $fork == 1 {
     $latitudeView = true
     turnleft 55
     penup
     forward $spacing
     turnThere 1
     forward 57 * $zoomValue
     pendown
     turnThere 3
     }
     else {
       if $fork == 2 {
        $latitudeView = false
        turnleft 35
        penup
        forward $spacing
        pendown
        turnThere 2
        }
        else {
          if $fork == 3 {
           $latitudeView = true
           turnleft 55
           penup
           forward $spacing
           turnThere 2
           forward 41 * $zoomValue
           pendown
           turnThere 1
           }
           else { turnThere 0 }
          }
       }
    }       
learn iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString {
    go $xPoint, $yPoint
    if not $newString { 
       if not $latitudeView {
        turnThere 3
        penup
        forward 41 * $zoomValue
        pendown
        }
        else {
          if not $cluster { $latitudeView  = false }
          turnThere 3
          penup
          forward 57 * $zoomValue
          pendown
          }
       }
      else {
         $newString = false
         if not $cluster { $latitudeView  = false }
         }
    direction 0
    }
learn faceDancer $entryOfDemo, $name, $system, $zoomValueT, $xPoint, $yPoint, $space, $newString, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $fork, $appearance {
     #tu awrinrhi  an ambivalence (‘a state of uncertainty or indecisiveness’; literally: ‘[around]/[with ring of] power’);
    if not $entryOfDemo {#initial point and number of turns
     for $step = 0 to $fork {
      iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $fork, $appearance
      pointIt $zoomValueT, $foreScripted, $afterScripted, $superScripted, $subScripted, $step, $appearance
      turnThere 0
      if $step != $fork {
       wait 2
       time $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $fork, $appearance
       }
      $newString = true
      }
     }
     else {
       for $step = 0 to $fork {
         moan $name, $system, $zoomValue, $xPoint, $yPoint, $space, $newString, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $step, $appearance
         turnThere 0
         if $step != $fork {
          wait 2
          time $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $fork, $appearance
          }
        $newString = true
        }
       }
    }
# fehu
#
#_ansuz_--may_be_related_to_a_compiler_
# pronunciation_--
# gethenian: ashe terrain: ansuz
learn ansuz $zoomValue, $appearance {
    if not $appearance {
     $a1 = mirrorIt 210
     $a2 = mirrorIt 199
     $a3 = mirrorIt 160
     }
     else {
       $a1 = 210
       $a2 = 199
       $a3 = 160
       }
    $l1 = 42 * $zoomValue
    penup
    forward $l1
    pendown
    $l2 = 41 * $zoomValue
    $l3 = 19 * $zoomValue
    $l4 = 12 * $zoomValue
    $l5 = 17 * $zoomValue
    turnleft 180
    forward $l1
    penup
    turnleft 180
    forward $l2
    turnleft $a1
    pendown
    forward $l3
    penup
    turnleft $a2
    forward $l4
    pendown
    turnleft $a3
    forward $l5
    }
#_ray
#
learn iPenErase $brush {
    $solvingBrush = $brush + 2
    penwidth $solvingBrush
    setColor 2#dbg
    }
learn iPenMark $brush {
    penwidth $brush
    setColor 1
    }
#
# ashe ansuz
#
#_sowilo
# pronunciation_--
# gethenian: sov terrain: sowulo sowilo
learn sowilo $zoomValue, $appearance {
    if not $appearance {
     $a1 = mirrorIt 164
     $a2 = mirrorIt 104
     $a3 = mirrorIt 257
     }
     else {
       $a1 = 164
       $a2 = 104
       $a3 = 257
       }
    $l1 = 17 * $zoomValue
    penup
    forward 39 * $zoomValue
    if $appearance {
     turnleft 270
     forward 6 * $zoomValue
     turnleft 90
     }
     else {
     turnleft 90
     forward 6 * $zoomValue
     turnleft 270
       }
    pendown
    $l2 = 7 * $zoomValue
    $l3 = 19 * $zoomValue
    turnleft $a1
    forward $l1
    turnleft $a2
    forward $l2
    turnleft $a3
    forward $l3
    }
# sov sowulo sowilo
#
#_laguz
# pronunciation_--
# gethenian: rthi terrain: laguz
learn laguz $zoomValue, $appearance {
    if not $appearance {
     $a1 = mirrorIt 210
     }
     else {
       $a1 = 210
       }
    $l1 = 42 * $zoomValue
    penup
    forward $l1
    if $appearance {
     turnleft 270
     forward 4 * $zoomValue
     turnleft 90
     }
     else {
       turnleft 90
       forward 2 * $zoomValue
       turnleft 270
       }
    pendown
    $l2 = 41 * $zoomValue
    $l3 = 15 * $zoomValue
    turnleft 180
    forward $l1
    penup
    turnleft 180
    forward $l2
    pendown
    turnleft $a1
    forward $l3
    }
# rthi laguz
#
#_jera
# pronunciation_--
# gethenian: yera terrain: jera
learn jera $zoomValue, $appearance {
    if not $appearance {
     $a1 = mirrorIt 155
     $a2 = mirrorIt 50
     $a3 = mirrorIt 164
     $a4 = mirrorIt 195
     $a5 = mirrorIt 310
     }
     else {
       $a1 = 155
       $a2 = 50
       $a3 = 164
       $a4 = 195
       $a5 = 310
       }
    penup
    forward 43 * $zoomValue
    if $appearance {
     turnleft 270
     forward 7 * $zoomValue
     turnleft 90
     }
     else {
       turnleft 90
       forward 4 * $zoomValue
       turnleft 270
       }
    pendown
    $l1 = 15 * $zoomValue
    $l2 = 12 * $zoomValue
    $l3 = 16 * $zoomValue
    $l4 = 17 * $zoomValue
    turnleft $a1
    forward $l1
    turnleft $a2
    forward $l1
    penup
    turnleft $a3
    forward $l2
    pendown
    turnleft $a4
    forward $l3
    turnleft $a5
    forward $l4
    }
learn turnThere $switch {
    if $switch == 0 { direction 0 }
     else {
       if $switch == 1 {  direction 90 }
        else {
          if $switch == 2 { direction 180 }
           else {
             if $switch == 3 { direction 270 }
              else {
                if $switch == 4 { direction 45 }
                 else {
                   if $switch == 5 { direction 315 }
                    else {
                      if $switch == 6 { direction 225 }
                       else { direction 135 }
                      }
                   }
                }
             }
          }
       }
    }
#
#injecting_funnies_into_yera [a cursor]
learn circle $zoomValue {
    turnright 90
    forward 7 * $zoomValue
    for $n = 1 to 36 {
       turnleft 10
       forward 3 * $zoomValue
       } 
    turnleft 90
    }
#
learn pointIt $zoomValue, $foreScripted, $afterScripted, $superScripted, $subScripted, $forkL, $appearance {
    setColor 3
    penup
    forward 4.5 * $zoomValue
    if not $appearance {
     turnleft 90
     forward 11 * $zoomValue
     turnright 90
     }
    $zoomValueC = cryptic 0, $zoomValue
    pendown
    circle $zoomValue
    penup
    if $foreScripted or $afterScripted {
#if any improper call does occur this stuff defaults to 7
     forward 18 * $zoomValue
     if $foreScripted and $superScripted { turnThere ringStack 4, $forkL }
      else {
        if $afterScripted and $superScripted { turnThere ringStack 5, $forkL }
         else {
           if $afterScripted and $subScripted { turnThere ringStack 6, $forkL }
            else { turnThere ringStack 7, $forkL }
           }
        }
     }
     else {
       turnleft 4
       forward 10 * $zoomValue
       pendown
       }
    wunjo $zoomValueC, $appearance
    setColor 1
    }
learn ringStack $pointer, $forkRing {#or maybe ordered ring {4, 5, 6, 7}
    $entryPoint = $pointer
    repeat $forkRing {
        $entryPoint = $entryPoint + 1
        if $entryPoint == 8 { $entryPoint = 4 }
        }
    return $entryPoint 
    }
learn setColor $colorScheme {
    if not $colorScheme {
     pencolor $backgroundR, $backgroundG, $backgroundB
     }
     else {
        if $colorScheme == 1 {
         pencolor $runeColorR, $runeColorG, $runeColorB
         }
         else {
           if $colorScheme == 2 {
            pencolor $letterColorR, $letterColorG, $letterColorB
            }
            else {
              if $colorScheme == 3 {
               pencolor $systemColorR, $systemColorG, $systemColorB
               }
              }
           }#to expand it in a future
        }
    }
#injecting_moan_into_yera [don`t even ask why]
learn moan $name, $system, $zoomValue, $xPoint, $yPoint, $space, $newString, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $fork, $appearance { 
   if $name == 1 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     ihwaz $zoomValue, $appearance
     }
   if $name == 2 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     berkanan $zoomValue, $appearance
     }
   if $name == 3 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     gebo $zoomValue
     }
   if $name == 4 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     tiwaz $zoomValue
     }
   if $name == 5 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     mannaz $zoomValue
     }
   if $name == 6 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     othila $zoomValue, $appearance
     }
   if $name == 7 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     naudiz $zoomValue, $appearance
     }
   if $name == 8 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     algiz $zoomValue
     }
   if $name == 9 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     thurisaz $zoomValue
     }
   if $name == 10 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     uruz $zoomValue, $appearance
     }
   if $name == 11 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     ingwaz $zoomValue
     }
   if $name == 12 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     isaz $zoomValue
     }
   if $name == 13 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     dagaz $zoomValue
     }
   if $name == 14 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     wunjo $zoomValue, $appearance
     }
   if $name == 15 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     raido $zoomValue, $appearance
     }
   if $name == 16 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     fehu $zoomValue, $appearance
     }
   if $name == 17 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     ansuz $zoomValue, $appearance
     }
   if $name == 18 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     sowilo $zoomValue, $appearance
     }
   if $name == 19 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     laguz $zoomValue, $appearance
     }
   if $name == 20 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     jera $zoomValue, $appearance
     }
   if $name == 21 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     ehwaz $zoomValue
     }
   if $name == 22 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     perd $zoomValue
     }
   if $name == 23 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     kaunan $zoomValue
     }
   if $name == 24 {
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $appearance
     hagalaz $zoomValue, $appearance
     }
   }
# yera jera
#
#_ehwaz
# pronunciation_--
# gethenian: eyw terrain: ehwaz
learn ehwaz $zoomValue {
    penup
    turnleft 90
    forward 8 * $zoomValue
    turnleft 270
    pendown
    $l1 = 41 * $zoomValue
    $l2 = 18 * $zoomValue
    forward $l1
    turnleft 220
    forward $l2
    turnleft 95
    forward $l2
    turnleft 225
    forward $l1
    }
# eyw ehwaz
#
#_perd
# pronunciation_--
# gethenian: ponwe terrain: perdro perd
learn perd $zoomValue {
    $l1 = 18 * $zoomValue
    $l2 = 21 * $zoomValue
    $l3 = 40 * $zoomValue
    penup
    forward $l3
    turnleft 270
    forward 18 * $zoomValue
    turnleft 90
    pendown
    turnleft 145
    forward $l1
    turnleft 255
    forward $l2
    turnleft 140
    forward $l3
    turnleft 140
    forward $l2
    turnleft 260
    forward $l1
    }
# ponwe perdro perd
#
#_kaunan
#_--is_related_to_ansuz_module_
# pronunciation_--
# gethenian: ken terrain: kenaz kaunan
learn kaunan $zoomValue {
    penup
    forward 43 * $zoomValue
    turnleft 270
    forward 8 * $zoomValue
    turnleft 90
    pendown
    $l1 = 24 * $zoomValue
    $l2 = 26 * $zoomValue
    turnleft 153
    forward $l1
    turnleft 50
    forward $l2
    }
# ken kenaz kaunan
#
#_hagalaz
# pronunciation_--
# gethenian: aisha terrain: hagala hagalaz
learn hagalaz $zoomValue, $appearance {
    if not $appearance {
     $a1 = mirrorIt 205
     $a2 = mirrorIt 155
     }
     else {
       $a1 = 205
       $a2 = 155
       }
    if $appearance {
     penup
     turnleft 90
     forward 4 * $zoomValue
     turnleft 270
     pendown
     }
     else {
     penup
     turnleft 270
     forward 4 * $zoomValue
     turnleft 90
     pendown
       }
    $l1 = 40 * $zoomValue
    $l2 = 43 * $zoomValue
    forward $l1
    turnleft $a1
    forward $l2
    turnleft $a2
    forward $l1
    }
# aisha hagala hagalaz
#
#main--demo
reset
spritehide
$backgroundR = 0
$backgroundG = 0
$backgroundB = 0
$runeColorR = 0
$runeColorG = 163
$runeColorB = 255
$letterColorR = 255
$letterColorG = 64
$letterColorB = 64
$systemColorR = 0
$systemColorG = 255
$systemColorB = 0
canvascolor $backgroundR, $backgroundG, $backgroundB
#penwidth 7
pencolor $runeColorR, $runeColorG, $runeColorB
#global_variables_(in_recent_implementation_an_explicit_declaration_
#_______in_functions_(in_parameters_list)_may_be_omitted*_--irulan)
$appearance = true
#cannot make it scalable yet... but i have tried that for only one call
$defaultZoom = 3
$zoomValueT = cryptic 1, $defaultZoom
$system = true
$xPoint = 815
$yPoint = 70 * $zoomValueT
$switch = 0#*_--irulan_(does_it_make_an_ambiguity_--see_'global_variables'_comment_earlier)_
$latitudeView = false
$forkIt = 0
$cluster = false
$space = false
$name = 0
$entryOfDemo = 0
#1 * 
canvassize 886, 1251
penwidth $zoomValueT
# oyerem runes
$newString = true
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
hagalaz $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
algiz $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
ansuz $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
berkanan $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
tiwaz $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
dagaz $zoomValueT
$newString = true
$xPoint = 815
$yPoint = 155 * $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
ehwaz $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
fehu $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
gebo $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
ingwaz $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
isaz $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
ihwaz $zoomValueT, $appearance
$newString = true
$xPoint = 815
$yPoint = 240 * $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
kaunan $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
mannaz $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
naudiz $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
othila $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
perd $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
raido $zoomValueT, $appearance
$newString = true
$xPoint = 815
$yPoint = 325 * $zoomValueT
#$forkIt = 1
#$zoomValueT = cryptic 0, $defaultZoom
#$superScripted = true
#$foreScripted = true
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
laguz $zoomValueT, $appearance
$zoomValueT = cryptic 0, $defaultZoom
$forkIt = 1
$newString = true
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
sowilo $zoomValueT, $appearance
$forkIt = 0
# $latitudeView = false
$zoomValueT = cryptic 1, $defaultZoom
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
thurisaz $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
uruz $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
wunjo $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
jera $zoomValueT, $appearance
#
# thonri oyer empty
turnThere 0
$a = 2048 + 1024
$b = 0
$n = 0
$fixBits = 4
$size = 2
$sheetB = 0
size $a, $n
$b = $n
$lenght = $b / $size
$height = $a / $size
go ($lenght / 2), (($height / 4) + $height / 2 )
#
#_an_initialization_
penup
turnleft 270
size ($height / 32), $n
$sheetB = $n
forward $sheetB * 2
$wirPointerX = getx
$wirPointerY = gety
$ingPointerX = 0
$ingPointerY = 0
$isaPointerX = 0
$isaPointerY = 0
#
turnleft 120
#
$counter = 3
pendown
while $counter {
    forward $sheetB * 4
    $counter = $counter - 1
    if $counter == 2 {
     $ingPointerX = getx
     $ingPointerY = gety
     }
    if $counter == 1 {
     $isaPointerX = getx
     $isaPointerY = gety
     }
    turnleft 120
    }
setColor 3#
container $sheetB, $fixBits, $wirPointerX, $wirPointerY
$newString = true
$xPoint = 815
$yPoint = 405 * $zoomValueT
#a cursor
$foreScripted = false
$afterScripted = true
$superScripted = false
$subScripted = true
$forkIt = 2
$appearance = false
faceDancer $entryOfDemo, $name, $system, $zoomValueT, $xPoint, $yPoint, $space, $newString, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $forkIt, $appearance
$entryOfDemo = 1
$name = 20
$name = 16
$name = 20
exit
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
pointIt $zoomValueT, $foreScripted, $afterScripted, $superScripted, $subScripted, $forkIt, $appearance
turnThere 0
time $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
$newString = true
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $appearance
pointIt $zoomValueT, $foreScripted, $afterScripted, $superScripted, $subScripted, $forkIt, $appearance
exit
fontsize 40
print $xPoint
forward 60
print $yPoint
forward 60
print $zoomValueT
exit





          if $cluster and $latitudeView {}#to make bindings


# $pattern,
#_moan

#learn moan $name, $system, $zoomValue, $xPoint, $yPoint, $space, $newline, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $fork, $appearance, $shiftValue, $toCapitalize {
#
#
#






























#_logic
#_inheritance
#_method
#_issue
#_dissolve
#
#_interface
#_dispatch
#_moan
#_funnies
#_ray
#_frame
#_factor
#_glacierMirror
#_kill
#
#_samples
#_framesOfBuffers
#_renga
#
```
