# treefingers
digital calligraphy application for gethenian variation of runic script [elder futhark]  
used by karhidish Handdarra followers

- it is written on kTurtle script
- to make it running you would need working kTurtle IDE (a part of KDE project)
- simply open .turtle file from IDE and the interpreter would run it for you
- it is a demo version; the variant published in this README.md produces B4 output
- because of my dyscalculia i had had a blunder with print sizes: [this] one was supposed to output B4 sheet but another [deleted] one was to output A4 sheet (i had forgotten that so i had scaled the B4 sheet up); now i had switched to a scalable solution by removing some magic numbers
- you may read the source code in .html format as well
- there are .pdf files available if you would like using demo script's output for an artwork item
- temporarily you may see `my raw comments` here that are not intended to be a documentation, it's just my way of coding. after my switch to developing next major version [2.1] those messy artifacts will be removed
- i have no time for maintenance work; everything recent is at `main`; intermediate versions (ones between number bumps) go to these places for seeing diffs: here is [version 2-0-7](source/ver-2-0-x/README.md) and its [HTML representation](open-in-browser/rolling-preview/treefingers.html) (if you want to read it with the syntax highlighting)
- you can visit [`treefingers` project's GitHub Pages](https://irulancorrino.github.io/treefingers/), you will find its source code with syntax highlighting there (current version and archive tree)
- you can take a look at our [gallery](pictures.md)

## ISSUES
  - [ ] the animation blinks (on repeated elements, because they are erased between two consecutive frames) <img alt="updated script`s output B4" title="treefingers (v2_0_3, B4)" src="https://github.com/user-attachments/assets/7fcef47a-6244-4efb-8059-a58dfb6e0523" width="400" />
  - [ ] in an animation, between two sequences, there is an eraser step missing (like between `fehu` and `yera` at the image above)
  - [ ] eraser functionality misses the point a little bit
  - [ ] with freshly introduced (`[2-0-6]`) typing functionality `$shadow` is either calculated or passed wrongly or the pipe is broken somwhere
  - [ ] somehow the color change for the overlay is not inherited
  - [ ] weirdly but my scaling test executes two more frames (#38 & #39); had found that by an accident, after missing the frame #36 while making the gif (and now i see not all variants are realised and there are more of redundant frame pairs)
  - [ ] i am stuck with development of file format (i want it to be searchable ...maybe i would use `valkey` or something ...i was going to design bitfields-based format)

#### code and pics

<img width="720" alt="treefingers sequence from v2_0_4-preview-5" title="testing version: 2-0-4-preview-5" src="https://github.com/user-attachments/assets/1116a753-455c-4a8e-a016-5a2bd5c71a2c" />
<img width="720" title="treefingers  2_0_5 locator test" src="https://github.com/user-attachments/assets/6a2854bc-78d2-4187-830d-5049c3ae7e06" />

   - [ ] to add pictures from v2-0-7

```
#treefingers 2.0.7 digital calligraphy application for runic script [elder futhark]
#    Copyright (C) 2014-2026  irulanCorrino
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
# ----fork_lock ----mirror_lock [may/should they set boundaries?] ----bloom? *****demos: bit fields; mouse mock; cryptic page; styles editor***** to add more properties
# thonri oyer
# empty_by_irulan_corrino_
#_--[a field, an action (probably interface base)]
##_fractal_dimension
## _makes_series_--a_divide_to_b_is_sqrt_of_2_
learn size2 $a {#_________________________                                            or $latitudeHold?
       $n = $a / 1.414214 # sqrt 2 #  missing function should switch both $cluster and cryptic;           $setBoundary; maybe $boundaryType [4] (& a function);
       return $n#      ^for setting up the cluster^ .*__*cue points*                                                            $majorMember; to store last member(s) size and
       }#              runes should set their [8 or 4] boundaries if are major members                                             to select $spacing basing on the sane value
#                                 dynamically selected rules for newly entered cluster members           ^setBoundary is looking better being a function; BOTH
learn size $a, $n {#_____critical_point:_______ spatial orientation of minor members should be a modifier to $setBoundary or $boundaryType
       $n = $a / 1.414214 # sqrt 2#       left * 15 to 1; 0; -1 to -15 * right; down * 15 to 1; 0; -1 to -15 * up :: critical_point locates to upper or loertird of a major member
       }#                                       if not ( $cluster and $latitudeHold ) { $latitudeView  = false } or to replace a former with the latter? a major hole again?
#                                               makes 10 bit ::  makes 21 bit :: 1 binding bit (bound/unbound member of the cluster)
learn line $base, $iteration {# 7 forbidden states and 24 runes make 5 bit; cluster member 4 bit; [environment 20 bit;] orientation 2 bit; mirror 1 bit
       $stepLength = 4 * $base / $iteration# is a member; is minor member; is superscripted; is forescripted                              27 free bit in a forbidden state
       return $stepLength# forbidden states NAR:
       }# next is a cluster; next is a rune; next is blooming cluster; next is a cluster @new line; next is blooming cluster @new line; next is a rune @new line; next is a number
#                                5 forbidden states and 26 letters make 5 bit;  makes 21 bit; 6 free bit
learn shiftRight $value, $power {# major member references its position at the cluster, all major members and its own overlays; minor member references its position at the overlay, all members of its overlay and major member
       $c = 1#                                               cue points:
       $d = $value#                                             back margin (for minor member role; stacking)
       while $d > 2 {#                                          front margin (for minor member role; stacking)
            $c = $c + 1#                                        four boundaries (for major member role; accomodation)
            $d = $d / 2#                                      cue points are derived from absolute values by shifting their roles after the glyph's state
            }
       $power = $c
       }
#
learn iIterator $base, $fixBitIterator, $iteration, $x, $y, $runOnce {
#_a_field_(an_empty_rune)_--common_case_
       go $x, $y
       $markOfThirdStemX = 0
       $markOfThirdStemY = 0
       $stepLength = 0
       if $runOnce { $iteration = $iteration * 2 }
       penup
       $stepLength = line $base, $iteration
#tl 90 print $iteration tr 90
       forward $stepLength
       $mOfSecondStemX = getx
       $mOfSecondStemY = gety
       turnleft 60
       pendown
       if not $runOnce { $runOnce = true }
       lips $stepLength, $markOfThirdStemX, $markOfThirdStemY, $mOfSecondStemX, $mOfSecondStemY, $x, $y, $runOnce, $base, $fixBitIterator, $iteration
       }
#
learn fieldEntry $stepLength, $markOfThirdStemX, $markOfThirdStemY, $mOfSecondStemX, $mOfSecondStemY, $x, $y, $runOnce, $base, $fixBitIterator, $iteration, $entry {
       if $entry == 1 {# print $iteration
        if $absense { setColor 7 }
         else { setColor 4 }
        iIterator $base, $fixBitIterator, $iteration, $x, $y, $runOnce
        setColor 2
        }
        else {
          if $entry == 2 {# print $iteration
           if $absense { setColor 7 }
            else { setColor 5 }
           iIterator $base, $fixBitIterator, $iteration, $mOfSecondStemX, $mOfSecondStemY, $runOnce
           setColor 2
           }
           else {# print $iteration
             if $absense { setColor 7 }
              else { setColor 6 }
             iIterator $base, $fixBitIterator, $iteration, $markOfThirdStemX, $markOfThirdStemY, $runOnce
             setColor 2
             }
          }
       }
#
learn lips $stepLength, $markOfThirdStemX, $markOfThirdStemY, $mOfSecondStemX, $mOfSecondStemY, $x, $y, $runOnce, $base, $fixBitIterator, $iteration {
        $entry = 0
        $f = 0
        repeat 3 {
             $f = $f + 1
             forward $stepLength
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
                fieldEntry $stepLength, $markOfThirdStemX, $markOfThirdStemY, $mOfSecondStemX, $mOfSecondStemY, $x, $y, $runOnce, $base, $fixBitIterator, $iteration, $entry
                }
          }
       }
#
learn container $fixBits {
       $fixBitIterator = $fixBits * 2
       $base = $sheetB
       $x = $wirPointerX
       $y = $wirPointerY 
       $iteration = 2
       $runOnce = false
       iIterator $base, $fixBitIterator, $iteration, $x, $y, $runOnce
       }
learn thonriOyer $zoomValue {#[empty rune]
     turnThere 0
     $a = 8192 + 1024
     $b = 0
     $n = 0
     $fixBits = 4
     $size = 2
     $n = size2 $a
     $b = $n
     $length = $b / $size
     $height = $a / $size
#
#_an_initialization_
     penup
     turnleft 270
     $n = size2 ($height / 32)
     $sheetB = $n * $zoomValue / 2
     go $centerX, $overlayCenterY
     forward $sheetB * 2
     $wirPointerX = getx
     $wirPointerY = gety
#
#print $wirPointerX + "*" + $wirPointerY + "*wir"
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
#print $ingPointerX + "*" + $ingPointerY + "*ing"
           }
          if $counter == 1 {
           $isaPointerX = getx# costs some memory
           $isaPointerY = gety# is the same as for wir
#print $isaPointerX + "*" + $isaPointerY + "*isa"
           }
          turnleft 120
          }
#setColor 3#
     container $fixBits
     }

# thonri oyer empty
#
#_iywa
#_--[a compiler namespace]
# pronunciation_--
# gethenian: iywa terrain: ihwar i(h)waz ei(h)waz
learn iywa $zoomValue {
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
#_bessa
# pronunciation_--
# gethenian: bessa terrain: bercana berkanan
learn bessa $zoomValue {
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
#_gad
#_--[possibly a compiler]
# pronunciation_--
# gethenian: gad terrain: gedo gebo
learn gad $zoomValue {
     penup
     forward 38 * $zoomValue
     turnleft 90
     forward 8 * $zoomValue
     turnleft 270
     pendown
     $l1 = 42 * $zoomValue
     $l2 = 35 * $zoomValue
     $l3 = 45 * $zoomValue
     turnright 144
     forward $l1
     penup
     turnleft 144
     forward $l2
     pendown
     turnleft 144
     forward $l3
     }
# gad gedo gebo
#
#_chawa
# pronunciation_--
# gethenian: chawa terrain: teiwaz tiwaz
learn chawa $zoomValue {
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
#_mand
#_--[possibly a compiler]
# pronunciation_--
# gethenian: mand terrain: mannaz
learn mand $zoomValue {
     $l1 = 40 * $zoomValue
     penup
     forward $l1
     turnleft 270
     forward 19 * $zoomValue
     turnleft 90
     pendown
     $l2 = 47 * $zoomValue
     $l3 = 39 * $zoomValue
     $l4 = 48 * $zoomValue
     $l5 = 32 * $zoomValue
     $l6 = 17 * $zoomValue
     turnleft 180
     forward $l1
     penup
     turnleft 215
     forward $l2
     turnleft 145
     pendown
     forward $l3
     turnleft 146
     penup
     forward $l4
     pendown
     turnleft 157
     forward $l5
     penup
     turnleft 237
     forward $l6
     pendown
     turnright 122
     forward $l5
     }
# mand mannaz
#
#_othir
#_--[a mirror]
#_--[a compiler]
learn placeholder $system, $zoomValue, $fork, $forkLock {
#print $switch
     rememberIt $xPoint, $yPoint
     $lA = $magic * $zoomValue
     $lB = $figure * $zoomValue
     $spacing =(sqrt ( ($lA ^ 2) + ($lB ^ 2) ))
     if not $switch { switchMode $fork, $forkLock, $spacing, $zoomValue }
     if $system {#never use it in a text!!! #FEATURE: gem runs textual update optionally {grid || text || field}
        penwidth cryptic 2, $defaultZoom
        if $absense { setColor 7 }
         else { setColor 3 }
        forward $lA
        turnleft 90
        forward $lB
        turnleft 90
        forward $lA
        turnleft 90
        forward $lB
        if $switch {
         penwidth cryptic 1, $defaultZoom
         if $absense { setColor 7 }
          else { setColor 8 }
         }
         else { setColor 1 }#for testing is 2 [glyph edit mode]
        }
     penup
     if not $system { turnleft 90 }
      else { turnleft 180 }
     forward $lB / 2
     if (not $appearance) and (not $mirrorLock) { backward $lB / 8 }
      else { forward $lB / 8 }
     turnleft 270
     forward $lA / 8
#setColor 1 [gem]
     pendown
#     if not $cluster { $latitudeView  = false }
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
learn othir $zoomValue {
     $a1 = 31
     $a2 = 65
     $a3 = 117
     $a4 = 70
     $l1 = 37 * $zoomValue
     $l2 = 22 * $zoomValue
     $l3 = 20 * $zoomValue
     $l4 = 39 * $zoomValue
     penup
     turnleft 130
     forward 6 * $zoomValue
     turnleft 230
     pendown
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
#_naue
# pronunciation_--
# gethenian: naue terrain: naupir naudiz
learn naue $zoomValue {
     if not $appearance {
      $a1 = mirrorIt 170
      $a2 = mirrorIt 67
      }
      else {
        $a1 = 170
        $a2 = 60
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
     turnleft 180
     forward $l1
     turnleft $a1
     penup
     forward $l2
     turnleft $a2
     pendown
     forward $l2
     }
# naue naupir naudiz
#
#_argir
#--_[possibly a compiler]
# pronunciation_--
# gethenian: argir terrain: algir algiz
learn argir $zoomValue {
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
     if not $crypticValue {# minor member bloom
      return $defaultZoom / 1.414214 # sqrt 2
      }
      else {
        if $crypticValue == 1 {# major member bloom
         return 2.121320 * $defaultZoom # 3 / sqrt 2
         }
         else {
           if $crypticValue == 2 {# major member
            return $defaultZoom
            }
            else {
              if $crypticValue == 3 {# minor member
               return 0.424264 * $defaultZoom # 3 / (5 * sqrt 2)
               }
               else {
                 if $crypticValue == 4 {# minor letter
                  return $defaultZoom / 5
                  }
                 }
              }
           }
        }
     }
learn time $system, $zoomValue, $fork, $forkLock {
     iLiner $zoomValue
     placeholder $system, $zoomValue, $fork, $forkLock
#     penup
     forward 14 * $zoomValue
     turnleft 90
     if (not $appearance) and (not $mirrorLock) { forward 5 * $zoomValue }
      else { backward 5 * $zoomValue }
     turnright 90
     pendown
     iPenErase $figure * $zoomValue
     forward  ($figure * 0.36 * $zoomValue)
     iPenMark $zoomValue, 1
     }
learn scribe $letter, $zoomValue {
     
     if $letter {
      if $letter == "a" {
       print "a"
       }
      if $letter == "b" {
       print "b"
       }
      if $letter == "c" {
       print "c"
       }
      if $letter == "d" {
       print "d"
       }
      if $letter == "e" {
       penup
       turnleft 90
       forward 1 * $zoomValue
       turnleft 270
       forward 24 * $zoomValue
       pendown
       $l1 = 41 * $zoomValue
       $l2 = 18 * $zoomValue
       turnleft 270
       forward $l2
       turnleft 140
       forward $l2
       turnleft 100
       forward $l1
       turnleft 135
       forward $l1
       }
      if $letter == "f" {
       print "f"
       }
      if $letter == "g" {
       print "g"
       }
      if $letter == "h" {
       print "h"
       }
      if $letter == "i" {
       print "i"
       }
      if $letter == "j" {
       print "j"
       }
      if $letter == "k" {
       print "k"
       }
      if $letter == "m" {
       print "m"
       }
      if $letter == "n" {
       print "n"
       }
      if $letter == "o" {
       print "o"
       }
      if $letter == "p" {
       print "p"
       }
      if $letter == "q" {
       print "q"
       }
      if $letter == "r" {
       print "r"
       }
      if $letter == "s" {
       print "s"
       }
      if $letter == "t" {
       print "t"
       }
      if $letter == "u" {
       print "u"
       }
      if $letter == "v" {
       print "v"
       }
      if $letter == "w" {
       print "w"
       }
      if $letter == "x" {
       print "x"
       }
      if $letter == "y" {
       print "y"
       }
      }
      else {
#        schritte
        }
     }
learn sense $oddity, $z {
     if not $z { return "''move||' 'switch||'-'back||'='set" }
      else {
        if not $oddity {
         if $z == 1 { return "$defaultZoom=5" }
         if $z == 2 { return "''rotate||' 'mirror||'-'scale||'='set" }#-0&3
         if $z == 3 { return "''select||'='set" }#- !1!2 !R!S
         if $z == 4 { return "''continue||'='set" }#- !1!2 R!S
         if $z == 5 { return "will you give me a Cookie?" }
         if $z == 6 { return "''continue||' 'clean||'-'move||'='edit" }#the regular prompt
         if $z == 7 { return "''height||' 'width||'-'set||'='return" }
         if $z == 8 { return "''width||' 'back||'-'set||'='return" }
         if $z == 9 { return "''edit||' 'out||'-'styles||'='return" }#edit
         if $z == 10 { return "''rollback||' 'panout||'-'scroll||'='return" }#clean view; editor?
         if $z == 11 { return "''save||' 'load||'-'exit||'='return" }#out
         if $z == 12 { return "" }
         if $z == 13 { return "" }
         }
         else {
           if $z == 1 { return "" }
           if $z == 2 { return "" }
           }
        }
     }
learn frame $z {
     $oddity = mod $z, 2
     if not $z {
      $query = sense $oddity, $z
      $queryResult = ask $query
      return $queryResult
      }
      else {
        if not $oddity {
         $z = $z / 2
         $query = sense $oddity, $z
         $queryResult = ask $query
         return $queryResult
         }
         else {
           $z = ($z + 1) / 2
           $message = sense $oddity, $z
           message $message
           }
        }
     }
# argir algir algiz
#
#_thured
#_--[directionality of scripting]
# pronunciation_--
# gethenian: thured terrain: thurisaz
learn thured $zoomValue {
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
learn snap $entryWord {# get ready for making a GIF
     if $entryWord == 0 {message "snap!" wait 3}
     if $entryWord == 1 {wait 3 message "cursor turned"}
     if $entryWord == 2 {wait 3 message "glyph turned"}
     if $entryWord == 3 {wait 3 message "?"}
     }
# thured thurisaz
#
#_uru
# pronunciation_--
# gethenian: uru terrain: uruz
learn uru $zoomValue {
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
#_ingif 
#_--[possibly is a compiler]
# pronunciation_--
# gethenian: ingif terrain: ingwar ingwaz
learn ingif $zoomValue {
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
#_isa
# pronunciation_--
# gethenian: isa terrain: isa isaz
learn isa $zoomValue {
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
#_dawa
#_--[possibly a compiler]
# pronunciation_--
# gethenian: dawa terrain: dagaz
learn dawa $zoomValue {
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
#_wunyo
# pronunciation_--
# gethenian: wunyo terrain: wunjo
learn wunyo $zoomValue {
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
#_reith
# pronunciation_--
# gethenian: reith terrain: raido raidho
learn reith $zoomValue {
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
learn fehu $zoomValue {
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
learn switchMode $fork, $forkLock, $spacing, $zoomValue {#
     if $forkLock == 2 {
      $shadow = $figure * $zoomValue
      turnThere 0
      return
      }
     if $fork == 1 {
      $latitudeView = true
      $shadow = $magic * $zoomValue
      turnleft 55
      penup
      forward $spacing
      turnThere 1
      forward $magic * $zoomValue
      pendown
      turnThere 3
      }
      else {
        if $fork == 2 {
         if not $forkLock {#$fork == 0
          $latitudeView = false
          $shadow = $figure * $zoomValue
          turnleft 35
          penup
          forward $spacing
          pendown
          turnThere 2
          }
          else {
            $shadow = $figure * $zoomValue
            turnThere 0
            }
         }
         else {
           if $fork == 3 {
            if not $forkLock {
             $latitudeView = true
             $shadow = $magic * $zoomValue
             turnleft 55
             penup
             forward $spacing
             turnThere 2
             forward $figure * $zoomValue
             pendown
             turnThere 1
             }
             else {#$fork == 1
               $latitudeView = true
               $shadow = $magic * $zoomValue
               turnleft 55
               penup
               forward $spacing
               turnThere 1
               forward $magic * $zoomValue
               pendown
               turnThere 3
               }
             }
             else {
               $shadow = $figure * $zoomValue
               turnThere 0
               }
           }
        }
     }       
learn iLiner $zoomValue {
#print $switch
     go $xPoint, $yPoint
     if not $newString {
      if ($switch == 1) or ($switch == -1) {
      direction 210
      }
      else {
        if ($switch == 2) or ($switch == -2) {
         turnThere 3
         }
         else {
           if ($switch == 3) or ($switch == -3) {
            direction 330
            }
            else { turnThere 3 }
           }
        }
      penup
      if $switch >= 0 { forward $shadow }
      pendown 
      direction 0
      }
      else {
        direction 0
        $newString = false
        }
#          if not $cluster { $latitudeView  = false }# ?_i guess it was intended for inheriting major element's cue points_????
     if ($switch == 1) or ($switch == -1) {
      turnleft 60
      $shadow = $figure * $zoomValue
      }
      else {
        if ($switch == 2) or ($switch == -2) {
         $shadow = $figure * $zoomValue
         }
         else {
           if ($switch == 3) or ($switch == -3) {
            turnleft 300
            $shadow = $figure * $zoomValue
            }
           }
        }
     }
#print  $shadow + "*" + $zoomValue
learn faceDancer $entryOfDemo, $system, $zoomValue, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $fork {
      #tu awrinrhi  an ambivalence (‘a state of uncertainty or indecisiveness’; literally: ‘[around]/[with ring of] power’);
     if not $entryOfDemo {#initial point and number of turns
      $forkLock = 0
      $mirrorLock = false
      for $step = 0 to $fork {
       iLiner $zoomValue
       placeholder $system, $zoomValue, 0, $forkLock
#snap 1
       pointIt $zoomValue, $foreScripted, $afterScripted, $superScripted, $subScripted, $step
       turnThere 0
       if $step != $fork {
#snap 3
        wait 2
        time $system, $zoomValue, 0, $forkLock
        }
       $newString = true
       }
      }
      else {
        for $step = 0 to $fork {
#snap 2
          $forkLock = moan $system, $zoomValue, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $step
          turnThere 0
          if $step != $fork {
#snap 3
           wait 2
           time $system, $zoomValue, $step, $forkLock
           }
         }
         $newString = true
        }
     }
#_overlay
#_oyerem [runes]
learn oyerem $zoomValue {
     $name = 0
     $appearance = true
     for $branch = 1 to 3 {
        $switch = $branch# namespace matters
        for $arc = 1 to 4 {
           $newString = true
           if $branch == 3 {
            $xPoint = $wirPointerX + ($arc-1) * $magic * $zoomValue * 0.866025# sin 60
            $yPoint = $wirPointerY - ($arc-1) * $magic * $zoomValue / 2# sin 30
            }
            else {
              if $branch == 2 {
               $xPoint = $wirPointerX
               $yPoint = $isaPointerY + $magic * $zoomValue + $magic * ($arc-1) * $zoomValue
               }
               else {
                 $xPoint = $ingPointerX - ($arc-1) * $magic * $zoomValue * 0.866025# sin 60
                 $yPoint = $ingPointerY - ($arc-1) * $magic * $zoomValue / 2# sin 30
                 }
              }
           for $column = 1 to 2 {
              if not ($absense and $selectorActive) { $name = $name + 1 }
              $forkLock = moan $system, $zoomValue, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, 0
              $newString = false
              }
           }
        }
     }
# oyerem
#_factor
learn rine $zoomValue {
#_logic
     $newString = mod $name, 2
     if $name > 8 {
      $gush = mod $name, 8
      $branch = ($name - $gush) / 8#0, 1, 2
      if mod $gush, 2 { $arc = (($gush - 1) / 2) + 1 }
       else { $arc = $gush / 2 }
      if not $gush {
       $branch = $branch - 1
       $arc = 4
       }
      }
      else {
        $branch = 0
        if mod $name, 2 { $arc = (($name - 1) / 2) + 1 }
         else { $arc = $name / 2 }
        }
#_locator
     if $branch == 2 {
      $xPointL = $wirPointerX
      $yPointL = $wirPointerY
      $xPointL = $xPointL + ($arc-1) * $magic * $zoomValue * 0.866025# sin 60
      $yPointL = $yPointL - ($arc-1) * $magic * $zoomValue / 2# sin 30
      }
      else {
        if $branch == 1 {
         $xPointL = $isaPointerX + 4*$sheetB
         $yPointL = $isaPointerY
         $yPointL = $yPointL  + $magic * $zoomValue + $magic * ($arc-1) * $zoomValue
         }
         else {
           $xPointL = $ingPointerX
           $yPointL = $ingPointerY
           $xPointL = $xPointL - ($arc-1) * $magic * $zoomValue * 0.866025# sin 60
           $yPointL = $yPointL - ($arc-1) * $magic * $zoomValue / 2# sin 30
           }
        }
     $xPoint =  $xPointL
     $yPoint =  $yPointL
     $branch = ($branch + 1)
     return $branch
     }
# factor
# fehu
#
#_ashe
#_--[may be related to a compiler]
# pronunciation_--
# gethenian: ashe terrain: ansuz
learn ashe $zoomValue {
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
#     $solvingBrush = $brush + 2solvingB
     penwidth $brush
     setColor 0
     }
learn iPenMark $brush, $color {
     if $brush > .5 { penwidth $brush }
      else { penwidth .5 }
     setColor $color
     }
# ray
# ashe ansuz
#
#_sov
# pronunciation_--
# gethenian: sov terrain: sowulo sowilo
learn sov $zoomValue {
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
     $l1 = 21 * $zoomValue
     penup
     forward 44 * $zoomValue
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
     $l2 = 9 * $zoomValue
     $l3 = 25 * $zoomValue
     turnleft $a1
     forward $l1
     turnleft $a2
     forward $l2
     turnleft $a3
     forward $l3
     }
# sov sowulo sowilo
#
#_rthi
# pronunciation_--
# gethenian: rthi terrain: laguz
learn rthi $zoomValue {
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
#_yera
# pronunciation_--
# gethenian: yera terrain: jera
learn yera $zoomValue {
     if not $appearance {
      $a1 = mirrorIt 147
      $a2 = mirrorIt 65
      $a3 = mirrorIt 157
      $a4 = mirrorIt 202
      $a5 = mirrorIt 295
      }
      else {
        $a1 = 147
        $a2 = 65
        $a3 = 157
        $a4 = 202
        $a5 = 295
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
        forward 6 * $zoomValue
        turnleft 270
        }
     pendown
     $l1 = 15 * $zoomValue
     $l2 = 12 * $zoomValue
     $l3 = 16 * $zoomValue
     $l4 = 19 * $zoomValue
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
learn turnThere $turn {
     if $turn == 0 { direction 0 }
      else {
        if $turn == 1 {  direction 90 }
         else {
           if $turn == 2 { direction 180 }
            else {
              if $turn == 3 { direction 270 }
               else {
                 if $turn == 4 { direction 45 }
                  else {
                    if $turn == 5 { direction 315 }
                     else {
                       if $turn == 6 { direction 225 }
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
learn pointIt $zoomValue, $foreScripted, $afterScripted, $superScripted, $subScripted, $fork {
     setColor 9
     penup
     forward 4.5 * $zoomValue
     if not $appearance {
      turnleft 90
      forward 11 * $zoomValue
      turnright 90
      }
     $zoomValueC = $zoomValue / 3
     pendown
     circle $zoomValue
     penup
     if $foreScripted or $afterScripted {
#if any improper call does occur this stuff defaults to 7
      forward 18 * $zoomValue
      if $foreScripted and $superScripted { turnThere ringStack 4, $fork }
       else {
         if $afterScripted and $superScripted { turnThere ringStack 5, $fork }
          else {
            if $afterScripted and $subScripted { turnThere ringStack 6, $fork }
             else { turnThere ringStack 7, $fork }
            }
         }
      }
      else {
        turnleft 4
        forward 10 * $zoomValue
        pendown
        }
     wunyo $zoomValueC
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
learn ringZoom $pointer, $zoomRing {#ordered ring {0, 1, 2, 3, 4}
     $entryPoint = $pointer
     repeat $zoomRing {
         $entryPoint = $entryPoint + 1
         if $entryPoint > 4 { $entryPoint = 0 }
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
                else {
                  if $colorScheme == 4 {#flashswitch (cue)
                   pencolor $letterColorR, $brightColorG, $backgroundB
                   }
                   else {
                     if $colorScheme == 5 {
                      pencolor $letterColorR, $backgroundG, $runeColorB
                      }
                      else {
                        if $colorScheme == 6 {
                         pencolor $backgroundR, $brightColorG, $runeColorB
                         }
                         else {
                           if $colorScheme == 7 {
                            pencolor $absenseColorR, $absenseColorG, $absenseColorB
                            }
                            else {
                              if $colorScheme == 8 {#overlay runes
                               pencolor $brightColorR, $backgroundG, $brightColorB
                               }
                               else {
                                 if $colorScheme == 9 {#cursor
                                  pencolor $letterColorR, $runeColorG, $runeColorB
                                  }
                                 }#to expand it in a future
                              }
                           }
                        }
                     }
                  }
               }
            }
         }
     }
#injecting_moan_into_yera [don`t even ask why]
learn moan $system, $zoomValue, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $fork {
#print $switch
    if $name == 1 {
      $forkLock = 1
      $mirrorLock = false
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      iywa $zoomValue
      return $forkLock
      }
    if $name == 2 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      bessa $zoomValue
      return $forkLock
      }
    if $name == 3 {
      $forkLock = 2
      $mirrorLock = true
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      gad $zoomValue
      return $forkLock
      }
    if $name == 4 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      chawa $zoomValue
      return $forkLock
      }
    if $name == 5 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      mand $zoomValue
      return $forkLock
      }
    if $name == 6 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      othir $zoomValue
      return $forkLock
      }
    if $name == 7 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      naue $zoomValue
      return $forkLock
      }
    if $name == 8 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      argir $zoomValue
      return $forkLock
      }
    if $name == 9 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      thured $zoomValue
      return $forkLock
      }
    if $name == 10 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      uru $zoomValue
      return $forkLock
      }
    if $name == 11 {
      $forkLock = 1
      $mirrorLock = true
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      ingif $zoomValue
      return $forkLock
      }
    if $name == 12 {
      $forkLock = 1
      $mirrorLock = true
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      isa $zoomValue
      return $forkLock
      }
    if $name == 13 {
      $forkLock = 1
      $mirrorLock = true
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      dawa $zoomValue
      return $forkLock
      }
    if $name == 14 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      wunyo $zoomValue
      return $forkLock
      }
    if $name == 15 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      reith $zoomValue
      return $forkLock
      }
    if $name == 16 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      fehu $zoomValue
      return $forkLock
      }
    if $name == 17 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      ashe $zoomValue
      return $forkLock
      }
    if $name == 18 {
      $forkLock = 1
      $mirrorLock = false
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      sov $zoomValue
      return $forkLock
      }
    if $name == 19 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      rthi $zoomValue
      return $forkLock
      }
    if $name == 20 {
      $forkLock = 1
      $mirrorLock = false
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      yera $zoomValue
      return $forkLock
      }
    if $name == 21 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      eyw $zoomValue
      return $forkLock
      }
    if $name == 22 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      ponwe $zoomValue
      return $forkLock
      }
    if $name == 23 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      ken $zoomValue
      return $forkLock
      }
    if $name == 24 {
      $forkLock = 1
      $mirrorLock = false
      iLiner $zoomValue
      placeholder $system, $zoomValue, $fork, $forkLock
      aisha $zoomValue
      return $forkLock
      }
    }
# yera jera
#
#_eyw
# pronunciation_--
# gethenian: eyw terrain: ehwaz
learn eyw $zoomValue {
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
#_ponwe
# pronunciation_--
# gethenian: ponwe terrain: perdro perd
learn ponwe $zoomValue {
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
#_ken
#_--[is related to ashe module]
# pronunciation_--
# gethenian: ken terrain: kenaz kaunan
learn ken $zoomValue {
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
#_aisha
# pronunciation_--
# gethenian: aisha terrain: hagala hagalaz
learn aisha $zoomValue {
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
$magic = 57# this pair is screen resolution dependent
$figure = 41
$sheetB = 0
$wirPointerX = 0
$wirPointerY = 0
$ingPointerX = 0
$ingPointerY = 0
$isaPointerX = 0
$isaPointerY = 0
$backgroundR = 0
$backgroundG = 0
$backgroundB = 0
$runeColorR = 20
$runeColorG = 163
$runeColorB = 255
$letterColorR = 255
$letterColorG = 64
$letterColorB = 64
$systemColorR = 63
$systemColorG = 80
$systemColorB = 63
$brightColorR = 100
$brightColorG = 255
$brightColorB = 140
$absenseColorR = 80
$absenseColorG = 63
$absenseColorB = 80
canvascolor $backgroundR, $backgroundG, $backgroundB
$dZ = frame 2# no less then five!!! (except for the tiny screens: 1@{533x754 pixels}; .5@{267x377 pixels}; .25@{133x188 pixels})/* such a submissive comment --irulan */
if ($dZ >= .25) or ($dZ < 5) { $defaultZoom = $dZ }
 else { $defaultZoom = 5 }
$zoomValueT = cryptic 2, $defaultZoom
$shadow = $figure * $zoomValueT
$shadowStore = $shadow
$appearance = true
$system = true
$rowHeight = 3 * $magic * $zoomValueT
$switch = 0
$latitudeView = false
$forkIt = 0
$cluster = false
$space = false
$name = 0
$foreScripted = false
$afterScripted = true
$superScripted = false
$subScripted = true
$entryOfDemo = 0
$stringLimit = 12# to add horizontal scrolling; to default to `infinite string to scrolling rows` UI mode (`autosplitting`), to include fixed page, various zooming modes
$absense = false
$selectorActive = false
$xSize = round (($stringLimit + 1) * $figure * $zoomValueT)
$leftMargin = round ($figure * $zoomValueT / 2)
$rightMargin = $xSize - $leftMargin
$stringLength = $rightMargin - $leftMargin# no horizontal scrolling
$string = 0
$stringScroll = $rightMargin - round ($leftMargin / 8)# horizontal scrolling
$ySize = round ($xSize * 1.414214) #sqrt 2
$rowLimit = ($ySize - mod $ySize, $rowHeight) / $rowHeight# quantised scrolling
$topMargin = round ((mod $ySize, $rowHeight) / 2)
$bottomMargin = $ySize - $topMargin
$scrollHeight = $bottomMargin - round ($topMargin / 8)# smooth scrolling
$scroll = 0#? + $rowHeight * $row# to address the scroll
$centerX = round ($xSize / 2)
$overlayCenterY = $topMargin + round ($figure * 1.73205 + 2 * $magic) * $zoomValueT# to move it
canvassize $xSize, $ySize
fontsize 15 * $zoomValueT
$forkLock = 0
$mirrorLock = false
$newString = true
#
#_overlay
$overlay = true
$xPoint = $rightMargin
$yPoint = $bottomMargin
    $forge = true
while $overlay {
while true {
     $newStringStore = $newString
     $xPointStore = $xPoint
     $yPointStore = $yPoint
     if $forge {
      $foreScriptedTaken = false
      $afterScriptedTaken = false
      $superScriptedTaken = false
      $subScriptedTaken = false
      }
#$break = false
$zoomValueT = .95 * cryptic 3, $defaultZoom
iPenMark (cryptic 2, $defaultZoom), 7
thonriOyer $zoomValueT
#
iPenMark (cryptic 1, $defaultZoom), 8# 1 for small screens
$zoomValueT = cryptic 2, $defaultZoom
oyerem $zoomValueT
#
$cue = 1
$system = false
$newString = true
$name = 1
while $cue {
     $switch = rine $zoomValueT
     iPenMark (cryptic 2, $defaultZoom), 4#flashswitch
     $forkLock = moan $system, $zoomValueT, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, 0
     $switch = -1*$switch
#snap 0
     $cue = frame 0
     if $cue == "-" {
      iPenMark (cryptic 1, $defaultZoom), 8
      $forkLock = moan $system, $zoomValueT, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, 0
      $cue = 1
      if $name > 1 { $name = $name - 1 }
       else { $name = 24 }
      }
      else {
        if $cue == " " {
         iPenMark (cryptic 1, $defaultZoom), 8
         $forkLock = moan $system, $zoomValueT, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, 0
         $cue = 1
         $columnT = mod $name, 2
         if $name > 8 {
          $gushT = mod $name, 8
          $branchT = ($name - $gushT) / 8#0, 1, 2
          if not $gushT { $branchT = $branchT - 1 }
          }
          else { $branchT = 0 }
         if $columnT {
          if $branchT == 1 { $name = $name + 8 }
           else { $name = $name + 1 }
          }
          else {
            if $branchT == 1 { $name = $name - 1 }
             else {
               if $branchT == 2 { $name = $name - 17 }
                else { $name = $name + 8 }
               }
            }
         }
         else {
           if $cue == "=" {
            $cue = 0
            }
            else {
              iPenMark (cryptic 1, $defaultZoom), 8
              $forkLock = moan $system, $zoomValueT, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, 0
              $cue = 1
              if $name < 23 { $name = $name + 2 }
               else {
                 if $name == 23 { $name = 1 }
                  else { $name = 2 }
                 }
              }
           }
        }
     }# flashswitch
#
$smithTwiddle = 1
$switch = 0
$latitudeView = false#cluster
$forking = 0
$forkIt = 0
$appearanceHold = true
if $forge {
 $zoomLevel = 2
 $zoomLevelB = false
 }
while $smithTwiddle {
     $zoomValueT = cryptic $zoomLevel, $defaultZoom/2
     if $latitudeView {
      $xPoint = $isaPointerX + 3*$sheetB
      $yPoint = $isaPointerY - $magic * $zoomValueT / 6
      }
      else {
        $xPoint = $isaPointerX + 2.71*$sheetB
        $yPoint = $isaPointerY - $magic * $zoomValueT / 8
        }
     $newString = true
     iPenMark (cryptic 1, $defaultZoom), 4
     $forkLock = moan $system, $zoomValueT, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $forking
     $smithTwiddle = frame 4
     if $smithTwiddle == "-" {# R!S
      if $forge {
       $smithTwiddle = 1
       if $zoomLevelB {
        $zoomLevel = $zoomLevel - 1
        if $zoomLevel < 0 {
         $zoomLevel = 2
         $zoomLevelB = false
         }
        }
        else {
          $zoomLevel = $zoomLevel + 1
          if $zoomLevel > 3 {
           $zoomLevel = 1
           $zoomLevelB = true
           }
          }
       $selectorActive = true
       $absense = true
       }
      }
      else {
        if $smithTwiddle == " " {# !R!S
         $smithTwiddle = 1
         $appearanceHold = not $appearanceHold
         $selectorActive = false
         $absense = true
         }
         else {
           if $smithTwiddle == "=" {
            $smithTwiddle = 0
            }
            else {# !R!S
              $smithTwiddle = 1
              $forking = $forking + 1
              if $forking > 3 { $forking = 0 }
              $selectorActive = false
              $absense = true
              }
           }
        }
     $newString = true
     iPenMark (cryptic 1, $defaultZoom) + 2, 1
     $forkLock = moan $system, $zoomValueT, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $forking
     $appearance = $appearanceHold
     $forkIt = $forking

     }# smithTwiddle
     if $zoomLevel == 0 or $zoomLevel == 3 {
#
#- !1!2 !R!S $smithSelect = frame 6
      $cluster = true
      $shadowStore = $shadow
  #    if $latitudeView { $shadow = $magic * cryptic $zoomLevel, $defaultZoom }#no doubles! newStringChild?
  #     else { $shadow = $figure * cryptic $zoomLevel, $defaultZoom }
      $foreScriptedTaken = true
      $newStringChild = true
      $shadowChild = true

      $afterScriptedTaken = true
      $newStringChild = true
      $shadowChild = true

      $superScriptedTaken = true
      $newStringChild = true
      $shadowChild = true

      $subScriptedTaken = true
      $newStringChild = true
      $shadowChild = true

#
      $smithForge = frame 8#- !1!2 R!S
      if $smithForge == "=" { $forge = true }
       else { $forge = false }
                              $shadowChild = false
#

      }
     $switch = 0
     $newString = $newStringStore
     $zoomValueT = cryptic $zoomLevel, $defaultZoom
     $xPoint = $xPointStore
     $yPoint = $yPointStore# + $rowHeight * $row# to address the scroll
     $shadow = $shadowStore
     iPenMark (cryptic 2, $defaultZoom), 1
     $forkLock = moan $system, $zoomValueT, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $forkIt
     $shadowStore = $shadow
   
   
if not frame 10 { break }#OK
# { $break = true }
     }# while true {break}

if not frame 10 { break }
#    $shadowStore = $shadow
#if frame 2x { break }#style editor (or clean view (but regularly a scrolling))# paging too BTW (infinite scrolling or locked scrolling)
     }# overlay
if not ask "will you give me a Cookie?" { exit }# frame 10"set"
#
$switch = 0
fontsize 40 * $zoomValueT
clear
$zoomValueT = cryptic 2, $defaultZoom
iPenMark (cryptic 2, $defaultZoom), 1
$name = 0
for $row = 0 to 3 {
   $newString = true
   $xPoint = $rightMargin
   $yPoint = $rowHeight + $rowHeight * $row
   for $column = 1 to 6 {
      $name = $name + 1
      $forkLock = moan $system, $zoomValueT, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, 0
      $newString = false
      }
   }

#
$zoomValueT = cryptic 2, $defaultZoom
$row = 3
$xPoint = $rightMargin
$yPoint = $rowHeight + $rowHeight * $row
# thonri oyer [empty rune]
turnThere 0
$a = 8192 + 1024
$b = 0
$n = 0
$fixBits = 4
$size = 2
size $a, $n
$b = $n
$length = $b / $size
$height = $a / $size
#
#_an_initialization_
penup
turnleft 270
size ($height / 32), $n
$sheetB = $n * $zoomValueT / 2
go 2*$leftMargin + $sheetB, $yPoint
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
#setColor 3#
container $sheetB, $fixBits, $wirPointerX, $wirPointerY
#
$entryOfDemo = 1
$xPoint = $rightMargin - 7*$shadow
$yPoint = 2*$rowHeight
$zoomValueT =  cryptic 1, $defaultZoom
$newString = true
$forkIt = 4
$name = 6
iPenMark $zoomValueT, 1
faceDancer $entryOfDemo, $system, $zoomValueT, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $forkIt
if not ask "will you give me a Cookie?" { exit }
#
clear
$zoomValueT = cryptic 2, $defaultZoom
$shadow = $figure * $zoomValueT
iPenMark $zoomValueT, 1
$turns = 0
$frame = 0
#snap 0
repeat 4 {
for $scans = 1 to 5 {
repeat 2 {
$name = 0
clear
go 60, 60
turnThere 0
$frame = $frame + 1
for $row = 0 to 3 {
   $newString = true
   $xPoint = $rightMargin
   $yPoint = $rowHeight + $rowHeight * $row
   for $column = 1 to 6 {
      $name = $name + 1
      $zoomScan =  cryptic (ringZoom $scans, $column), $defaultZoom#round
      $forkLock = moan $system, $zoomScan, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $turns
      $newString = false
if $frame == 7 or $frame == 21 {
fontsize 10 * $zoomValueT
print (ringZoom $scans, $column) + "*" +  cryptic (ringZoom $scans, $column), $defaultZoom#round
fontsize 40 * $zoomValueT }
      }
   }
#message "say 'Cookie!'" 
print $frame
if $frame == 7 {snap 0}
if $frame == 21 {snap 0}
         $appearance = not $appearance
         }#repeat 2
   }
         $turns = $turns + 1
         }#repeat 4

#exit


#
$zoomValueT = cryptic 2, $defaultZoom
$shadow = $figure * $zoomValueT
$row = 3
$xPoint = $rightMargin
$yPoint = $rowHeight + $rowHeight * $row
# thonri oyer [empty rune]
turnThere 0
$a = 8192 + 1024
$b = 0
$n = 0
$fixBits = 4
$size = 2
size $a, $n
$b = $n
$length = $b / $size
$height = $a / $size
#
#_an_initialization_
penup
turnleft 270
size ($height / 32), $n
$sheetB =  ($n * $zoomValueT / 2)
go 2*$leftMargin + $sheetB, $yPoint
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
#setColor 3#
container $sheetB, $fixBits, $wirPointerX, $wirPointerY
$newString = true
#a cursor
$entryOfDemo = 0
$foreScripted = false
$afterScripted = true
$superScripted = false
$subScripted = true
$forkIt = 3
$appearance = true
$zoomValueT = cryptic 2, $defaultZoom
#snap 0 #uncomment 'snaps' in this function's definition for step mode (and comment its own 'waits' out)
faceDancer $entryOfDemo, $system, $zoomValueT, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $forkIt
$entryOfDemo = 1
$xPoint = $rightMargin - 2*$shadow
$yPoint = $rowHeight + $rowHeight * $row
$name = 20
faceDancer $entryOfDemo, $system, $zoomValueT, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $forkIt
$xPoint = $rightMargin - 3*$shadow
$yPoint = $rowHeight + $rowHeight * $row
$name = 16
faceDancer $entryOfDemo, $system, $zoomValueT, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $forkIt
$xPoint = $rightMargin - 4*$shadow
$yPoint = $rowHeight + $rowHeight * $row
$zoomValueT =  cryptic 1, $defaultZoom#round
$forkIt = 4
$name = 6
faceDancer $entryOfDemo, $system, $zoomValueT, $space, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $forkIt
message "say 'Cookie!'" 

exit

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
