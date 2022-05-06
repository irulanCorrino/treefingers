# treefingers
digital calligraphy application for gethenian variation of runic script [elder futhark]  
used by karhidish Handdarra followers

- it is written on kTurtle script
- to make it running you would need working kTurtle IDE (a part of KDE project)
- simply open .turtle file from IDE and the interpreter would run it for you
- it is a demo version; the variant published in this README.md produces A4 output
- there are two variants around here: [this] one outputting A4 sheet and another one outputting B4 sheet
- you may read the source code in .html format as well
- there are .pdf files available if you would like using demo script's output for an artwork item (B4 sticker variant is formatted in two versions --with and without margins for a printing)
![treefingers  high contrast](https://user-images.githubusercontent.com/98284211/167228348-850b979a-7bd5-455a-8d3a-48537e4681e9.png)


>```
>kturtle-script-v1.0
>#treefingers 2.0 [corrected version of 1.0] digital calligraphy application for runic script [elder futhark]
>#    Copyright (C) 2014  irulanCorrino
>#
>#    This program is free software: you can redistribute it and/or modify
>#    it under the terms of the GNU General Public License as published by
>#    the Free Software Foundation, either version 3 of the License, or
>#    (at your option) any later version.
>#
>#    This program is distributed in the hope that it will be useful,
>#    but WITHOUT ANY WARRANTY; without even the implied warranty of
>#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
>#    GNU General Public License for more details.
>#
>#    You should have received a copy of the GNU General Public License
>#    along with this program.  If not, see <https://www.gnu.org/licenses/>.
>#____________________________________________________________________________
>#
># thonri oyer empty_by_irulan_corrino_ --a field, an action (probably interface base)
>##_fractal_dimension
>## _makes_series_--a_divide_to_b_is_sqrt_of_2_
>@(learn) size2 $a {
>       $n = $a / @(sqrt) 2
>       @(return) $n
>       }
>#
>@(learn) size $a@(,) $n {
>       $n = $a / @(sqrt) 2
>       }
>#
>@(learn) line $base@(,) $iteration {
>       $stepLenght = @(round) ( 4 * $base / $iteration )
>       @(return) $stepLenght
>       }
>#
>@(learn) shiftRight $value@(,) $power {
>       $c = 1
>       $d = $value
>       @(while) $d > 2 {
>            $c = $c + 1
>            $d = $d / 2
>            }
>       $power = $c
>       }
>#
>@(learn) iIterator $base@(,) $fixBitIterator@(,) $iteration@(,) $x@(,) $y@(,) $runOnce {
>#_a_field_(an_empty_rune)_--common_case_
>       @(go) $x@(,) $y
>       $markOfThirdStemX = 0
>       $markOfThirdStemY = 0
>       $stepLenght = 0
>       @(if) $runOnce { $iteration = $iteration * 2 }
>       @(penup)
>       $stepLenght = line $base@(,) $iteration
>       @(forward) $stepLenght
>       $mOfSecondStemX = @(getx)
>       $mOfSecondStemY = @(gety)
>       @(turnleft) 60
>       @(pendown)
>       @(if) @(not) $runOnce { $runOnce = @(true) }
>       lips $stepLenght@(,) $markOfThirdStemX@(,) $markOfThirdStemY@(,) $mOfSecondStemX@(,) $mOfSecondStemY@(,) $x@(,) $y@(,) $runOnce@(,) $base@(,) $fixBitIterator@(,) $iteration
>       }
>#
>@(learn) fieldEntry $stepLenght@(,) $markOfThirdStemX@(,) $markOfThirdStemY@(,) $mOfSecondStemX@(,) $mOfSecondStemY@(,) $x@(,) $y@(,) $runOnce@(,) $base@(,) $fixBitIterator@(,) $iteration@(,) $entry {
>       @(if) $entry == 1 { iIterator $base@(,) $fixBitIterator@(,) $iteration@(,) $x@(,) $y@(,) $runOnce }
>         @(else) {
>           @(if) $entry == 2 { iIterator $base@(,) $fixBitIterator@(,) $iteration@(,) $mOfSecondStemX@(,) $mOfSecondStemY@(,) $runOnce }
>            @(else) { iIterator $base@(,) $fixBitIterator@(,) $iteration@(,) $markOfThirdStemX@(,) $markOfThirdStemY@(,) $runOnce }
>              }
>           }
>       }
>#
>@(learn) lips $stepLenght@(,) $markOfThirdStemX@(,) $markOfThirdStemY@(,) $mOfSecondStemX@(,) $mOfSecondStemY@(,) $x@(,) $y@(,) $runOnce@(,) $base@(,) $fixBitIterator@(,) $iteration {
>        $entry = 0
>        $f = 0
>        @(repeat) 3 {
>             $f = $f + 1
>             @(forward) $stepLenght
>             @(if) $f == 2 { 
>                $markOfThirdStemX = @(getx)
>                $markOfThirdStemY = @(gety)
>                }
>             @(turnleft) 120
>             }
>        @(turnleft) 300
>        @(if) @(not) ($iteration == $fixBitIterator) {
>           @(repeat) 3 {
>                $entry = $entry + 1
>                fieldEntry $stepLenght@(,) $markOfThirdStemX@(,) $markOfThirdStemY@(,) $mOfSecondStemX@(,) $mOfSecondStemY@(,) $x@(,) $y@(,) $runOnce@(,) $base@(,) $fixBitIterator@(,) $iteration@(,) $entry
>                }
>          }
>       }
>#
>@(learn) container $sheetB@(,) $fixBits@(,) $wirPointerX@(,) $wirPointerY {
>       $fixBitIterator = $fixBits * 2
>       $base = $sheetB
>       $iteration = 2
>       $runOnce = @(false)
>       iIterator $base@(,) $fixBitIterator@(,) $iteration@(,) $wirPointerX@(,) $wirPointerY@(,) $runOnce
>       }
># thonri oyer empty
>#
>#_i(h)waz
>#_--a_compiler_namespace_
># pronunciation_--
># gethenian: iywa terrain: ihwar i(h)waz ei(h)waz
>@(learn) ihwaz $zoomValue@(,) $appearance {
>     @(if) @(not) $appearance {
>      $a1 = mirrorIt 15
>      $a2 = mirrorIt 165
>      $a3 = mirrorIt 199
>      }
>      @(else) {
>        $a1 = 15
>        $a2 = 165
>        $a3 = 199
>        }
>     $l1 = 10 * $zoomValue
>     $l2 = 40 * $zoomValue
>     @(penup)
>     @(forward) 32 * $zoomValue
>     @(if) $appearance {
>      @(turnleft) 270
>      @(forward) 10 * $zoomValue
>      @(turnleft) 90
>      }
>      @(else) {
>        @(turnleft) 90
>        @(forward) 8 * $zoomValue
>        @(turnleft) 270
>        }
>     @(pendown)
>     $l3 = 12 * $zoomValue
>     @(turnleft) $a1
>     @(forward) $l1
>     @(turnleft) $a2
>     @(forward) $l2
>     @(turnleft) $a3
>     @(forward) $l3     
>     }
># iywa ihwar i(h)waz ei(h)waz
>#
>#_berkanan
># pronunciation_--
># gethenian: bessa terrain: bercana berkanan
>@(learn) berkanan $zoomValue@(,) $appearance {
>     @(if) @(not) $appearance {
>      $a1 = mirrorIt 21
>      $a2 = mirrorIt 69
>      $a3 = mirrorIt 111
>      $a4 = mirrorIt 107
>      }
>      @(else) {
>        $a1 = 21
>        $a2 = 69
>        $a3 = 111
>        $a4 = 107
>        }
>     $l1 = 40 * $zoomValue
>     @(penup)
>     @(forward) $l1
>     @(if) $appearance {
>      @(turnleft) 270
>      @(forward) 5 * $zoomValue
>      @(turnleft) 90
>      }
>      @(else) {
>        @(turnleft) 90
>        @(forward) 2 * $zoomValue
>        @(turnleft) 270
>        }
>     @(pendown)
>     $l2 = 12 * $zoomValue
>     $l3 = 5 * $zoomValue
>     $l4 = 9 * $zoomValue
>     @(turnleft) 180
>     @(forward) $l1
>     @(penup)
>     @(backward) $l1
>     @(pendown)
>     @(turnleft) $a1
>     @(forward) $l2
>     @(turnright) $a2
>     @(forward) $l3
>     @(turnleft) $a3
>     @(forward) $l4
>     @(turnright) $a4
>     @(forward) $l2
>     }
># bessa bercana berkanan
>#
>#_gebo
>#_--possibly_a_compiler_
># pronunciation_--
># gethenian: gad terrain: gedo gebo
>@(learn) gebo $zoomValue {
>     @(penup)
>     @(forward) 38 * $zoomValue
>     @(turnleft) 90
>     @(forward) 10 * $zoomValue
>     @(turnleft) 270
>     @(pendown)
>     $l1 = 48 * $zoomValue
>     $l2 = 37 * $zoomValue
>     $l3 = 52 * $zoomValue
>     @(turnright) 134
>     @(forward) $l1
>     @(penup)
>     @(turnleft) 144
>     @(forward) $l2
>     @(pendown)
>     @(turnleft) 130
>     @(forward) $l3
>     }
># gad gedo gebo
>#
>#_tiwaz
># pronunciation_--
># gethenian: chawa terrain: teiwaz tiwaz
>@(learn) tiwaz $zoomValue {
>     $l1 = 40 * $zoomValue
>     @(penup)
>     @(forward) $l1
>     @(turnleft) 270
>     @(forward) 7 * $zoomValue
>     @(turnleft) 90
>     @(pendown)
>     $l2 = 10 * $zoomValue
>     $l3 = 12 * $zoomValue
>     @(turnleft) 180
>     @(forward) $l1
>     @(penup)
>     @(backward) $l1
>     @(pendown)
>     @(turnleft) 19
>     @(forward) $l2
>     @(penup)
>     @(backward) $l2
>     @(pendown)
>     @(turnright) 40
>     @(forward) $l3
>     }
># chawa teiwaz tiwaz
>#
>#_mannaz
>#_--possibly_a_compiler_
># pronunciation_--
># gethenian: mand terrain: mannaz
>@(learn) mannaz $zoomValue {
>     $l1 = 40 * $zoomValue
>     @(penup)
>     @(forward) $l1
>     @(turnleft) 270
>     @(forward) 19 * $zoomValue
>     @(turnleft) 90
>     @(pendown)
>     $l2 = 44 * $zoomValue
>     $l3 = 32 * $zoomValue
>     $l4 = 50 * $zoomValue
>     $l5 = 35 * $zoomValue
>     $l6 = 16 * $zoomValue
>     @(turnleft) 180
>     @(forward) $l1
>     @(penup)
>     @(turnleft) 225
>     @(forward) $l2
>     @(turnleft) 135
>     @(pendown)
>     @(forward) $l3
>     @(turnleft) 142
>     @(penup)
>     @(forward) $l4
>     @(pendown)
>     @(turnleft) 160
>     @(forward) $l5
>     @(penup)
>     @(turnleft) 237
>     @(forward) $l6
>     @(pendown)
>     @(turnright) 118
>     @(forward) $l3
>     }
># mand mannaz
>#
>#_othila _--mirror_
>#_a_compiler_
>@(learn) placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance {
>     rememberIt $xPoint@(,) $yPoint
>     $lA = 57
>     $lB = @(round) (size2 $lA)
>     $lA = $lA * $zoomValue
>     $lB = $lB * $zoomValue
>     $spacing = @(round) (@(sqrt) ( ($lA ^ 2) + ($lB ^ 2) ))
>     switchMode $latitudeView@(,) $fork@(,) $spacing@(,) $zoomValue
>     @(if) $system {
>        @(pencolor) 0@(,) 255@(,) 0
>        @(forward) $lA
>        @(turnleft) 90
>        @(forward) $lB
>        @(turnleft) 90
>        @(forward) $lA
>        @(turnleft) 90
>        @(forward) $lB
>        @(pencolor) 0@(,) 163@(,) 255
>        }
>     @(penup)
>     @(if) @(not) $system { @(turnleft) 90 }
>      @(else) { @(turnleft) 180 }
>     @(forward) @(round) ($lB / 2)
>     @(if) $appearance { @(forward) @(round) ($lB / 8) }
>      @(else) { @(backward) @(round) ($lB / 8) }
>     @(turnleft) 270
>     @(forward) @(round) ($lA / 8)
>     @(pendown)
>     }
>@(learn) mirrorIt $value {#
>     $angle = 360 - $value
>     @(return) $angle
>     }
>@(learn) rememberIt $xPoint@(,) $yPoint {
>     $xPoint = @(getx)
>     $yPoint = @(gety)
>     }
># pronunciation_--
># gethenian: othir terrain: othala othila
>@(learn) othila $zoomValue {
>     $a1 = 31
>     $a2 = 65
>     $a3 = 117
>     $a4 = 78
>     $l1 = 28 * $zoomValue
>     $l2 = 28 * $zoomValue
>     $l3 = 19 * $zoomValue
>     $l4 = 45 * $zoomValue
>     @(turnright) $a1
>     @(forward) $l1
>     @(turnleft) $a2
>     @(forward) $l2
>     @(turnleft) $a3
>     @(forward) $l3
>     @(turnleft) $a4
>     @(forward) $l4
>     }
># othir othala othila
>#
>#_naudiz
># pronunciation_--
># gethenian: naue terrain: naupir naudiz
>@(learn) naudiz $zoomValue@(,) $appearance {
>     @(if) @(not) $appearance {
>      $a1 = mirrorIt 170
>      $a2 = mirrorIt 67
>      }
>      @(else) {
>        $a1 = 170
>        $a2 = 67
>        }
>     $l1 = 43 * $zoomValue
>     @(penup)
>     @(forward) $l1
>     @(if) $appearance {
>      @(turnleft) 270
>      @(forward) 8 * $zoomValue
>      @(turnleft) 90
>      }
>      @(else) {
>      @(turnleft) 90
>      @(forward) 12 * $zoomValue
>      @(turnleft) 270
>        }
>     @(pendown)
>     $l2 = 29 * $zoomValue
>     $l3 = 31 * $zoomValue
>     @(turnleft) 180
>     @(forward) $l1
>     @(turnleft) $a1
>     @(penup)
>     @(forward) $l2
>     @(turnleft) $a2
>     @(pendown)
>     @(forward) $l3
>     }
># naue naupir naudiz
>#
>#_algiz
>#--_possibly_a_compiler_
># pronunciation_--
># gethenian: argir terrain: algir algiz
>@(learn) algiz $zoomValue {
>     $l1 = 42 * $zoomValue
>     @(penup)
>     @(forward) $l1
>     @(turnleft) 270
>     @(forward) 6 * $zoomValue
>     @(turnleft) 90
>     @(pendown)
>     $l2 = 41 * $zoomValue
>     $l3 = 18 * $zoomValue
>     @(turnleft) 180
>     @(forward) $l1
>     @(penup)
>     @(turnleft) 190
>     @(forward) $l2
>     @(pendown)
>     @(turnright) 167
>     @(forward) $l3
>     @(turnleft) 115
>     @(forward) $l3
>     }
># argir algir algiz
>#
>#_thurisaz
># pronunciation_--
># gethenian: thured terrain: thurisaz
>@(learn) thurisaz $zoomValue {
>     $l1 = 43 * $zoomValue
>     @(penup)
>     @(forward) $l1
>     @(turnleft) 270
>     @(forward) $zoomValue
>     @(turnleft) 90
>     @(pendown)
>     $l2 = 41 * $zoomValue
>     $l3 = 26 * $zoomValue
>     $l4 = 28 * $zoomValue
>     @(turnleft) 180
>     @(forward) $l1
>     @(penup)
>     @(backward) $l2
>     @(pendown)
>     @(turnleft) 38
>     @(forward) $l3
>     @(turnleft) 285
>     @(forward) $l4
>     }
># thured thurisaz
>#
>#_uruz
># pronunciation_--
># gethenian: uru terrain: uruz
>@(learn) uruz $zoomValue@(,) $appearance {
>     @(if) @(not) $appearance {
>      $a1 = mirrorIt 5
>      $a2 = mirrorIt 40
>      $a3 = mirrorIt 130
>      }
>      @(else) {
>        $a1 = 5
>        $a2 = 40
>        $a3 = 130
>        }
>     @(if) $appearance {
>      @(penup)
>      @(turnleft) 90
>      @(forward) 5 * $zoomValue
>      @(turnleft) 270
>      @(pendown)
>      }
>      @(else) {
>      @(penup)
>      @(turnleft) 270
>      @(forward) 5 * $zoomValue
>      @(turnleft) 90
>      @(pendown)
>        }
>     $l1 = 28 * $zoomValue
>     $l2 = 20 * $zoomValue
>     $l3 = 42 * $zoomValue
>     @(turnright) $a1
>     @(forward) $l1
>     @(turnright) $a2
>     @(forward) $l2
>     @(turnright) $a3
>     @(forward) $l3
>     }
># uru uruz
>#
>#_ingwaz 
>#_--possibly_is_a_compiler_
># pronunciation_--
># gethenian: ingif terrain: ingwar ingwaz
>@(learn) ingwaz $zoomValue {
>     $l1 = 25 * $zoomValue
>     @(penup)
>     @(forward) 41 * $zoomValue
>     @(turnleft) 90
>     @(forward) 8 * $zoomValue
>     @(turnleft) 270
>     @(pendown)
>     $l2 = 28 * $zoomValue
>     $l3 = 45 * $zoomValue
>     @(turnright) 140
>     @(forward) $l1
>     @(turnright) 75
>     @(forward) $l2
>     @(penup)
>     @(turnright) 165
>     @(forward) $l3
>     @(pendown)
>     @(turnleft) 175
>     @(forward) $l1
>     @(turnleft) 77
>     @(forward) $l2
>     }
># ingif ingwar ingwaz
>#
>#_isaz
># pronunciation_--
># gethenian: isa terrain: isa isaz
>@(learn) isaz $zoomValue {
>     $l1 = 42 * $zoomValue
>     @(penup)
>     @(forward) $l1
>     @(turnleft) 270
>     @(forward) 5 * $zoomValue
>     @(turnleft) 90
>     @(pendown)
>     @(turnleft) 180
>     @(forward) $l1
>     }
># isa isaz
>#
>#_dagaz
>#_--possibly_a_compiler
># pronunciation_--
># gethenian: dawa terrain: dagaz
>@(learn) dagaz $zoomValue {
>     $l1 = 42 * $zoomValue
>     @(penup)
>     @(forward) $l1
>     @(turnleft) 90
>     @(forward) 8 * $zoomValue
>     @(turnleft) 270
>     @(pendown)
>     $l2 = 47 * $zoomValue
>     $l3 = 40 * $zoomValue
>     $l4 = 45 * $zoomValue
>     @(turnleft) 180
>     @(forward) $l1
>     @(turnleft) 148
>     @(forward) $l2
>     @(turnright) 148
>     @(forward) $l3
>     @(turnright) 148
>     @(forward) $l4
>     }
># dawa dagaz
>#
>#_wunjo
># pronunciation_--
># gethenian: wunyo terrain: wunjo
>@(learn) wunjo $zoomValue@(,) $appearance {
>     @(if) @(not) $appearance {
>      $a1 = mirrorIt 223
>      $a2 = mirrorIt 263
>      }
>      @(else) {
>        $a1 = 223
>        $a2 = 263
>        }
>     $l1 = 43 * $zoomValue
>     @(penup)
>     @(forward) $l1
>     @(pendown)
>     $l2 = 41 * $zoomValue
>     $l3 = 18 * $zoomValue
>     $l4 = 16 * $zoomValue
>     @(turnleft) 180
>     @(forward) $l1
>     @(penup)
>     @(turnleft) 180
>     @(forward) $l2
>     @(pendown)
>     @(turnleft) $a1
>     @(forward) $l3
>     @(turnleft) $a2
>     @(forward) $l4
>     }
># wunyo wunjo
>#
>#_raido
># pronunciation_--
># gethenian: reith terrain: raido raidho
>@(learn) raido $zoomValue@(,) $appearance {
>     @(if) @(not) $appearance {
>      $a1 = mirrorIt 221
>      $a2 = mirrorIt 265
>      $a3 = mirrorIt 95
>      }
>      @(else) {
>        $a1 = 221
>        $a2 = 265
>        $a3 = 95
>        }
>     $l1 = 44 * $zoomValue
>     @(penup)
>     @(forward) $l1
>     @(pendown)
>     $l2 = 42 * $zoomValue
>     $l3 = 14 * $zoomValue
>     $l4 = 12 * $zoomValue
>     $l5 = 30 * $zoomValue
>     @(turnleft) 180
>     @(forward) $l1
>     @(penup)
>     @(turnleft) 180
>     @(forward) $l2
>     @(pendown)
>     @(turnleft) $a1
>     @(forward) $l3
>     @(turnleft) $a2
>     @(forward) $l4
>     @(turnleft) $a3
>     @(forward) $l5
>     }
># reith raido raidho
>#
>#_fehu
># pronunciation_--
># gethenian: fehu terrain: fehu
>@(learn) fehu $zoomValue@(,) $appearance {
>     @(if) @(not) $appearance {
>      $a1 = mirrorIt 162
>      $a2 = mirrorIt 168
>      $a3 = mirrorIt 190
>      }
>      @(else) {
>        $a1 = 162
>        $a2 = 168
>        $a3 = 190
>        }
>     $l1 = 41 * $zoomValue
>     @(penup)
>     @(forward) $l1
>     @(pendown)
>     $l2 = 46 * $zoomValue
>     $l3 = 23 * $zoomValue
>     $l4 = 21 * $zoomValue
>     $l5 = 26 * $zoomValue
>     @(turnleft) 180
>     @(forward) $l1
>     @(penup)
>     @(turnleft) $a1
>     @(forward) $l2
>     @(pendown)
>     @(turnleft) $a1
>     @(forward) $l3
>     @(penup)
>     @(turnleft) $a2
>     @(forward) $l4
>     @(pendown)
>     @(turnleft) $a3
>     @(forward) $l5
>     }
>@(learn) switchMode $latitudeView@(,) $fork@(,) $spacing@(,) $zoomValue {
>     @(if) $fork == 1 {
>      $latitudeView = @(true)
>      @(turnleft) 55
>      @(penup)
>      @(forward) $spacing
>      turnThere 1
>      @(forward) 57 * $zoomValue
>      @(pendown)
>      turnThere 3
>      }
>      @(else) {
>        @(if) $fork == 2 {
>         $latitudeView = @(false)
>         @(turnleft) 35
>         @(penup)
>         @(forward) $spacing
>         @(pendown)
>         turnThere 2
>         }
>         @(else) {
>           @(if) $fork == 3 {
>            $latitudeView = @(true)
>            @(turnleft) 55
>            @(penup)
>            @(forward) $spacing
>            turnThere 2
>            @(forward) 41 * $zoomValue
>            @(pendown)
>            turnThere 1
>            }
>            @(else) { turnThere 0 }
>           }
>        }
>     }       
>@(learn) iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString {
>     @(go) $xPoint@(,) $yPoint
>     @(if) @(not) $newString { 
>        @(if) @(not) $latitudeView {
>         turnThere 3
>         @(penup)
>         @(forward) 41 * $zoomValue
>         @(pendown)
>         }
>         @(else) {
>           turnThere 3
>           @(penup)
>           @(forward) 57 * $zoomValue
>           @(pendown)
>           }
>        }
>       @(else) { $newString = @(false) }
>     @(direction) 0
>     }
># fehu
>#
>#_ansuz_--may_be_related_to_a_compiler_
># pronunciation_--
># gethenian: ashe terrain: ansuz
>@(learn) ansuz $zoomValue@(,) $appearance {
>     @(if) @(not) $appearance {
>      $a1 = mirrorIt 210
>      $a2 = mirrorIt 199
>      $a3 = mirrorIt 160
>      }
>      @(else) {
>        $a1 = 210
>        $a2 = 199
>        $a3 = 160
>        }
>     $l1 = 42 * $zoomValue
>     @(penup)
>     @(forward) $l1
>     @(pendown)
>     $l2 = 41 * $zoomValue
>     $l3 = 19 * $zoomValue
>     $l4 = 12 * $zoomValue
>     $l5 = 17 * $zoomValue
>     @(turnleft) 180
>     @(forward) $l1
>     @(penup)
>     @(turnleft) 180
>     @(forward) $l2
>     @(turnleft) $a1
>     @(pendown)
>     @(forward) $l3
>     @(penup)
>     @(turnleft) $a2
>     @(forward) $l4
>     @(pendown)
>     @(turnleft) $a3
>     @(forward) $l5
>     }
># ashe ansuz
>#
>#_sowilo
># pronunciation_--
># gethenian: sov terrain: sowulo sowilo
>@(learn) sowilo $zoomValue@(,) $appearance {
>     @(if) @(not) $appearance {
>      $a1 = mirrorIt 164
>      $a2 = mirrorIt 104
>      $a3 = mirrorIt 257
>      }
>      @(else) {
>        $a1 = 164
>        $a2 = 104
>        $a3 = 257
>        }
>     $l1 = 17 * $zoomValue
>     @(penup)
>     @(forward) 39 * $zoomValue
>     @(if) $appearance {
>      @(turnleft) 270
>      @(forward) 6 * $zoomValue
>      @(turnleft) 90
>      }
>      @(else) {
>      @(turnleft) 90
>      @(forward) 6 * $zoomValue
>      @(turnleft) 270
>        }
>     @(pendown)
>     $l2 = 7 * $zoomValue
>     $l3 = 19 * $zoomValue
>     @(turnleft) $a1
>     @(forward) $l1
>     @(turnleft) $a2
>     @(forward) $l2
>     @(turnleft) $a3
>     @(forward) $l3
>     }
># sov sowulo sowilo
>#
>#_laguz
># pronunciation_--
># gethenian: rthi terrain: laguz
>@(learn) laguz $zoomValue@(,) $appearance {
>     @(if) @(not) $appearance {
>      $a1 = mirrorIt 210
>      }
>      @(else) {
>        $a1 = 210
>        }
>     $l1 = 42 * $zoomValue
>     @(penup)
>     @(forward) $l1
>     @(if) $appearance {
>      @(turnleft) 270
>      @(forward) 4 * $zoomValue
>      @(turnleft) 90
>      }
>      @(else) {
>        @(turnleft) 90
>        @(forward) 2 * $zoomValue
>        @(turnleft) 270
>        }
>     @(pendown)
>     $l2 = 41 * $zoomValue
>     $l3 = 15 * $zoomValue
>     @(turnleft) 180
>     @(forward) $l1
>     @(penup)
>     @(turnleft) 180
>     @(forward) $l2
>     @(pendown)
>     @(turnleft) $a1
>     @(forward) $l3
>     }
># rthi laguz
>#
>#_jera
># pronunciation_--
># gethenian: yera terrain: jera
>@(learn) jera $zoomValue@(,) $appearance {
>     @(if) @(not) $appearance {
>      $a1 = mirrorIt 155
>      $a2 = mirrorIt 50
>      $a3 = mirrorIt 164
>      $a4 = mirrorIt 195
>      $a5 = mirrorIt 310
>      }
>      @(else) {
>        $a1 = 155
>        $a2 = 50
>        $a3 = 164
>        $a4 = 195
>        $a5 = 310
>        }
>     @(penup)
>     @(forward) 43 * $zoomValue
>     @(if) $appearance {
>      @(turnleft) 270
>      @(forward) 7 * $zoomValue
>      @(turnleft) 90
>      }
>      @(else) {
>        @(turnleft) 90
>        @(forward) 4 * $zoomValue
>        @(turnleft) 270
>        }
>     @(pendown)
>     $l1 = 15 * $zoomValue
>     $l2 = 12 * $zoomValue
>     $l3 = 16 * $zoomValue
>     $l4 = 17 * $zoomValue
>     @(turnleft) $a1
>     @(forward) $l1
>     @(turnleft) $a2
>     @(forward) $l1
>     @(penup)
>     @(turnleft) $a3
>     @(forward) $l2
>     @(pendown)
>     @(turnleft) $a4
>     @(forward) $l3
>     @(turnleft) $a5
>     @(forward) $l4
>     }
>@(learn) turnThere $switch {
>     @(if) $switch == 0 { @(direction) 0 }
>      @(else) {
>        @(if) $switch == 1 {  @(direction) 90 }
>         @(else) {
>           @(if) $switch == 2 { @(direction) 180 }
>            @(else) {
>              @(if) $switch == 3 { @(direction) 270 }
>               @(else) {
>                 @(if) $switch == 4 { @(direction) 45 }
>                  @(else) {
>                    @(if) $switch == 5 { @(direction) 135 }
>                     @(else) {
>                       @(if) $switch == 6 { @(direction) 225 }
>                        @(else) { @(direction) 315 }
>                       }
>                    }
>                 }
>              }
>           }
>        }
>     }
>#
>#injecting_funnies_into_yera --disabled [no cursor]
>@(learn) circle $zoomValue {
>     @(for) $n = 1 @(to) 36 {
>        @(turnleft) 10
>        @(forward) 3 * $zoomValue
>        }
>     }
>#
>@(learn) pointIt $zoomValue@(,) $foreScripted@(,) $afterScripted@(,) $superScripted@(,) $subScripted@(,) $fork@(,) $appearance {
>     @(if) $foreScripted @(or) $afterScripted {
>      @(pendown)
>      @(forward) 17 * $zoomValue
>      @(if) $foreScripted @(and) $superScripted { turnThere 4 }
>       @(else) {
>         @(if) $afterScripted @(and) $superScripted { turnThere 7 }
>          @(else) {
>            @(if) $afterScripted @(and) $subScripted { turnThere 6 }
>             @(else) { turnThere 5 }
>            }
>         }
>      }
>      @(else) {
>        @(penup)
>        turnThere 0
>        @(forward) 17 * $zoomValue
>        @(pendown)
>        }
>     @(turnleft) 90
>     circle $zoomValue
>     $zoomValueC = @(round) ( $zoomValue / 3 )
>     iLiner $latitudeView@(,) $zoomValueC@(,) $xPoint@(,) $yPoint@(,) $newString
>     placeholder $system@(,) $zoomValueC@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>     wunjo $zoomValueC@(,) $appearance
>     }
># yera jera
>#
>#_ehwaz
># pronunciation_--
># gethenian: eyw terrain: ehwaz
>@(learn) ehwaz $zoomValue {
>     @(penup)
>     @(turnleft) 90
>     @(forward) 8 * $zoomValue
>     @(turnleft) 270
>     @(pendown)
>     $l1 = 41 * $zoomValue
>     $l2 = 18 * $zoomValue
>     @(forward) $l1
>     @(turnleft) 220
>     @(forward) $l2
>     @(turnleft) 95
>     @(forward) $l2
>     @(turnleft) 225
>     @(forward) $l1
>     }
># eyw ehwaz
>#
>#_perd
># pronunciation_--
># gethenian: ponwe terrain: perdro perd
>@(learn) perd $zoomValue {
>     $l1 = 18 * $zoomValue
>     $l2 = 21 * $zoomValue
>     $l3 = 40 * $zoomValue
>     @(penup)
>     @(forward) $l3
>     @(turnleft) 270
>     @(forward) 18 * $zoomValue
>     @(turnleft) 90
>     @(pendown)
>     @(turnleft) 145
>     @(forward) $l1
>     @(turnleft) 255
>     @(forward) $l2
>     @(turnleft) 140
>     @(forward) $l3
>     @(turnleft) 140
>     @(forward) $l2
>     @(turnleft) 260
>     @(forward) $l1
>     }
># ponwe perdro perd
>#
>#_kaunan
>#_--is_related_to_ansuz_module_
># pronunciation_--
># gethenian: ken terrain: kenaz kaunan
>@(learn) kaunan $zoomValue {
>     @(penup)
>     @(forward) 43 * $zoomValue
>     @(turnleft) 270
>     @(forward) 8 * $zoomValue
>     @(turnleft) 90
>     @(pendown)
>     $l1 = 24 * $zoomValue
>     $l2 = 26 * $zoomValue
>     @(turnleft) 153
>     @(forward) $l1
>     @(turnleft) 50
>     @(forward) $l2
>     }
># ken kenaz kaunan
>#
>#_hagalaz
># pronunciation_--
># gethenian: aisha terrain: hagala hagalaz
>@(learn) hagalaz $zoomValue@(,) $appearance {
>     @(if) @(not) $appearance {
>      $a1 = mirrorIt 205
>      $a2 = mirrorIt 155
>      }
>      @(else) {
>        $a1 = 205
>        $a2 = 155
>        }
>     @(if) $appearance {
>      @(penup)
>      @(turnleft) 90
>      @(forward) 4 * $zoomValue
>      @(turnleft) 270
>      @(pendown)
>      }
>      @(else) {
>      @(penup)
>      @(turnleft) 270
>      @(forward) 4 * $zoomValue
>      @(turnleft) 90
>      @(pendown)
>        }
>     $l1 = 40 * $zoomValue
>     $l2 = 43 * $zoomValue
>     @(forward) $l1
>     @(turnleft) $a1
>     @(forward) $l2
>     @(turnleft) $a2
>     @(forward) $l1
>     }
># aisha hagala hagalaz
>#
>#main--demo
>@(reset)
>@(spritehide)
>@(canvascolor) 0@(,) 0@(,) 0
>@(penwidth) 7
>@(pencolor) 0@(,) 163@(,) 255
>#global_variables_(in_recent_implemention_an_explicit_declaration_
>#_______in_functions_(in_parameters_list)_may_be_omitted*_--irulan)
>$appearance = @(true)
>$zoomValue = 2.4
>$system = @(true)
>$xPoint = 675
>$yPoint = 70 * $zoomValue
>$switch = 0#*_--irulan_(does_it_make_an_ambiguity_--see_'global_variables'_comment_earlier)_
>$latitudeView = @(false)
>$fork = 0
>#
>@(canvassize) 744@(,) 1052
>@(penwidth) 1 * $zoomValue
># oyerem runes
>$newString = @(true)
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>hagalaz $zoomValue@(,) $appearance
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>algiz $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>ansuz $zoomValue@(,) $appearance
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>berkanan $zoomValue@(,) $appearance
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>tiwaz $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>dagaz $zoomValue
>$newString = @(true)
>$xPoint = 675
>$yPoint = 155 * $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>ehwaz $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>fehu $zoomValue@(,) $appearance
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>gebo $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>ingwaz $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>isaz $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>ihwaz $zoomValue@(,) $appearance
>$newString = @(true)
>$xPoint = 675
>$yPoint = 240 * $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>kaunan $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>mannaz $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>naudiz $zoomValue@(,) $appearance
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>othila $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>perd $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>raido $zoomValue@(,) $appearance
>$newString = @(true)
>$xPoint = 675
>$yPoint = 325 * $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>laguz $zoomValue@(,) $appearance
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>sowilo $zoomValue@(,) $appearance
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>thurisaz $zoomValue
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>uruz $zoomValue@(,) $appearance
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>wunjo $zoomValue@(,) $appearance
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>jera $zoomValue@(,) $appearance
>#
># thonri oyer empty
>turnThere 0
>$a = 2048 + 1024
>$b = 0
>$n = 0
>$fixBits = 4
>$size = 2
>$sheetB = 0
>size $a@(,) $n
>$b = $n
>$lenght = $b / $size
>$height = $a / $size
>@(go) ($lenght / 2)@(,) (($height / 4) + $height / 2 - $height / 8 )
>#
>#_an_initialization_
>@(penup)
>@(turnleft) 270
>size ($height / 32)@(,) $n
>$sheetB = @(round) $n
>@(forward) $sheetB * 2
>$wirPointerX = @(getx)
>$wirPointerY = @(gety)
>$ingPointerX = 0
>$ingPointerY = 0
>$isaPointerX = 0
>$isaPointerY = 0
>#
>@(turnleft) 120
>#
>$counter = 3
>@(pendown)
>@(while) $counter {
>     @(forward) $sheetB * 4
>     $counter = $counter - 1
>     @(if) $counter == 2 {
>      $ingPointerX = @(round) @(getx)
>      $ingPointerY = @(gety)
>      }
>     @(if) $counter == 1 {
>      $isaPointerX = @(round) @(getx)
>      $isaPointerY = @(gety)
>      }
>     @(turnleft) 120
>     }
>@(pencolor) 0@(,) 255@(,) 0#
>container $sheetB@(,) $fixBits@(,) $wirPointerX@(,) $wirPointerY
>#
>@(exit)#no cursor --disabled feature
>#$zoomValue = 3
>$foreScripted = @(true)
>$afterScripted = @(false)
>$superScripted = @(true)
>$subScripted = @(false)
>$fork = 2
>$appearance = @(false)
>iLiner $latitudeView@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $newString
>placeholder $system@(,) $zoomValue@(,) $xPoint@(,) $yPoint@(,) $latitudeView@(,) $fork@(,) $appearance
>pointIt $zoomValue@(,) $foreScripted@(,) $afterScripted@(,) $superScripted@(,) $subScripted@(,) $fork@(,) $appearance
>@(exit)
>#_logic
>#_inheritance
>#_method
>#_issue
>#_dissolve
>#
>#_interface
>#_dispatch
>#_moan
>#_funnies
>#_ray
>#_frame
>#_factor
>#_glacierMirror
>#_kill
>#
>#_samples
>#_framesOfBuffers
>#_renga
>#
>```
