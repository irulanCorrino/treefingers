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
- temporarily you may see `my raw comments` here that are not intended to be a documentation, it's just my way of coding
- there's a mess with branches, please do not be too critical (and in previous versions i had things like `sqrt 2` instead of a calculated value)
- i have no time for maintenance work; everything recent is at `main`; intermediate versions (ones between number bumps) go to these places for seeing diffs: here is [a preview for version 2-0-4](source/ver-2-0-x/README.md) and its [HTML representation](open-in-browser/rolling-preview/treefingers.html) (if you want to read it with the syntax highlighting)
- after my switch to developing next major version [2.1] those messy artifacts (comments, branches) will be removed anyway
<img alt="treefingers sequence from v2_0_4-preview-5" title="testing version: 2-0-4-preview-5" src="https://github.com/user-attachments/assets/1116a753-455c-4a8e-a016-5a2bd5c71a2c" />

- ISSUES:
  - [ ] the animation blinks (on repeated elements, because they are erased between two consecutive frames) <img alt="updated script`s output B4" title="treefingers (v2_0_3, B4)" src="https://github.com/user-attachments/assets/7fcef47a-6244-4efb-8059-a58dfb6e0523" width="400" />
  - [ ] in an animation, between two sequences, there is an eraser step missing (like between `fehu` and `yera` at the image above)
  - [x] broken pipeline for sequencing glyphs <img width="172" title="this is from version 2-0-4 preview-0 (glyphs should go in rows in this test but they are stuck together)" alt="treefingers  2_0_4 actual broken pipeline" src="https://github.com/user-attachments/assets/121613f0-4015-4d90-af62-e62824d43935" /> <img width="172" title="2-0-4-preview-1 improvements: - can place glyph sequentially; - scaling works. issues: - addressing is broken (glyphs are misplaced if mirrored); - having a blunder (at very first call to glyph pipeline); - the lock against flipping symmetric glyphs is incomplete ('gad')" alt="treefingers  2_0_4 improvements-n-issues" src="https://github.com/user-attachments/assets/e6279b40-86f9-4f93-9687-2f2505bad849" /> is repaired <img width="172" title="2-0-4-preview-3 improvements: - a blunder at very first call to glyph pipeline is fixed; - the lock against flipping symmetric glyphs is functional ('gad'). issues: - addressing is broken (glyphs are misplaced if mirrored)" alt="treefingers  2_0_4 preview-3" src="https://github.com/user-attachments/assets/276cf337-33c5-4df7-83d0-c2bf39fdab3b" />
  - [ ] and i was very tired after a long period of dothe so had placed wrong image for previous list entry <img title="this is a forcible grouping, i assign $newString switch to 'true' on each iteration" width="172" alt="treefingers  2_0_4 broken scaling" src="https://github.com/user-attachments/assets/4aefc9bb-660f-4222-9ede-c25769c9ebba" /> ...the image looked more neat to a tired girl
  - [ ] addressing is broken (glyphs are misplaced if mirrored); currently i am testing this behavior [in 2-0-4-preview-5, check the topmost gif]
  - [ ] weirdly but my test executes two more frames (#38 & #39); had found that by an accident, after missing the frame #36 while making the gif
  - [ ] not mirroring a glyph at `moan` [sic] makes the animation go astray (`'hand crafted' layout`) <img title="v2-0-3, animation layout problem" width="172" alt="treefingers  2_0_3 not mirrored animation" src="https://github.com/user-attachments/assets/911f17f9-4a2e-433b-b8af-7099870fecac" />
  - [ ] i am stuck with development of file format (i want it to be searchable ...maybe i would use `valkey` or something ...i was going to design bitfields-based format)


```
#treefingers 2.0.4 [preview-5] digital calligraphy application for runic script [elder futhark]
#    Copyright (C) 2014-2025  irulanCorrino
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
       $stepLenght = 4 * $base / $iteration# is a member; is minor member; is superscripted; is forescripted                              27 free bit in a forbidden state
       return $stepLenght# forbidden states NAR:
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
#_iywa
#_--[a compiler namespace]
# pronunciation_--
# gethenian: iywa terrain: ihwar i(h)waz ei(h)waz
learn iywa $zoomValue, $appearance {
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
learn bessa $zoomValue, $appearance {
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
learn placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance {
     rememberIt $xPoint, $yPoint
     $lA = $magic * $zoomValue
     $lB = $figure * $zoomValue
     $spacing =(sqrt ( ($lA ^ 2) + ($lB ^ 2) ))
     switchMode $latitudeView, $fork, $forkLock, $spacing, $zoomValue
     if $system {
        setColor 3
        forward $lA
        turnleft 90
        forward $lB
        turnleft 90
        forward $lA
        turnleft 90
        forward $lB
        setColor 2#for testing is 2
        }
#     penup
     if not $system { turnleft 90 }
      else { turnleft 180 }
     forward $lB / 2
     if $appearance { forward $lB / 8}
      else { backward $lB / 8}
     turnleft 270
     forward $lA / 8
setColor 1#
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
     turnleft 123
     forward 16
     turnleft 237
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
learn naue $zoomValue, $appearance {
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
learn time $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance, $newString {
     $lA = 46 * 0.471405 * $zoomValue # (√2)÷3
     iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
     placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
     penup
     forward 10 * $zoomValue
     turnleft 90
     forward 5 * $zoomValue
     turnright 90
     pendown
     iPenErase 2 * $lA * $zoomValue / 3 # 
     forward $lA
     iPenMark $zoomValue
     }
learn shadow $latitudeView {#to remove if unused
     if $latitudeView { return $magic }
      else { return $figure }
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
learn uru $zoomValue, $appearance {
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
learn wunyo $zoomValue, $appearance {
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
learn reith $zoomValue, $appearance {
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
learn switchMode $latitudeView, $fork, $forkLock, $spacing, $zoomValue {#
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
learn iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString {
     go $xPoint, $yPoint
     if not $newString { 
        if not $latitudeView {
         turnThere 3
         penup
         forward $shadow
         pendown
         }
         else {
#           if not $cluster { $latitudeView  = false print $cluster }
           turnThere 3
           penup
           forward $shadow
           pendown
           }
        }
        else { $newString = false }
#          if not $cluster { $latitudeView  = false }# ?_i guess it was intended for inheriting major element's cue points_????
     direction 0
     }
#print  $shadow + "*" + $zoomValue
learn faceDancer $entryOfDemo, $name, $system, $zoomValue, $xPoint, $yPoint, $space, $newString, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $fork, $appearance {
      #tu awrinrhi  an ambivalence (‘a state of uncertainty or indecisiveness’; literally: ‘[around]/[with ring of] power’);
     if not $entryOfDemo {#initial point and number of turns
      $forkLock = 0
      $mirrorLock = false
      for $step = 0 to $fork {
       iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
       placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, 0, $forkLock, $appearance
#snap 1
       pointIt $zoomValue, $foreScripted, $afterScripted, $superScripted, $subScripted, $step, $appearance
       turnThere 0
       if $step != $fork {
#snap 3
        wait 2
        time $system, $zoomValue, $xPoint, $yPoint, $latitudeView, 0, $forkLock, $appearance, $newString
        }
       $newString = true
       }
      }
      else {
        for $step = 0 to $fork {
#snap 2
          $forkLock = moan $name, $system, $zoomValue, $xPoint, $yPoint, $space, $newString, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $step, $appearance
          turnThere 0
          if $step != $fork {
#snap 3
           wait 2
           time $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $step, $forkLock, $appearance, $newString
           }
         }
         $newString = true
        }
     }
# fehu
#
#_ashe
#_--[may be related to a compiler]
# pronunciation_--
# gethenian: ashe terrain: ansuz
learn ashe $zoomValue, $appearance {
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
#_sov
# pronunciation_--
# gethenian: sov terrain: sowulo sowilo
learn sov $zoomValue, $appearance {
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
learn rthi $zoomValue, $appearance {
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
learn yera $zoomValue, $appearance {
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
     $zoomValueC = $zoomValue / 3
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
     wunyo $zoomValueC, $appearance
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
               }
            }#to expand it in a future
         }
     }
#injecting_moan_into_yera [don`t even ask why]
learn moan $name, $system, $zoomValue, $xPoint, $yPoint, $space, $newString, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $fork, $appearance { 
    if $name == 1 {
      $forkLock = 1
      $mirrorLock = false
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      iywa $zoomValue, $appearance
      return $forkLock
      }
    if $name == 2 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      bessa $zoomValue, $appearance
      return $forkLock
      }
    if $name == 3 {
      $forkLock = 2
      $mirrorLock = true
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      gad $zoomValue
      return $forkLock
      }
    if $name == 4 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      chawa $zoomValue
      return $forkLock
      }
    if $name == 5 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      mand $zoomValue
      return $forkLock
      }
    if $name == 6 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      othir $zoomValue
      return $forkLock
      }
    if $name == 7 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      naue $zoomValue, $appearance
      return $forkLock
      }
    if $name == 8 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      argir $zoomValue
      return $forkLock
      }
    if $name == 9 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      thured $zoomValue
      return $forkLock
      }
    if $name == 10 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      uru $zoomValue, $appearance
      return $forkLock
      }
    if $name == 11 {
      $forkLock = 1
      $mirrorLock = true
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      ingif $zoomValue
      return $forkLock
      }
    if $name == 12 {
      $forkLock = 1
      $mirrorLock = true
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      isa $zoomValue
      return $forkLock
      }
    if $name == 13 {
      $forkLock = 1
      $mirrorLock = true
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      dawa $zoomValue
      return $forkLock
      }
    if $name == 14 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      wunyo $zoomValue, $appearance
      return $forkLock
      }
    if $name == 15 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      reith $zoomValue, $appearance
      return $forkLock
      }
    if $name == 16 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      fehu $zoomValue, $appearance
      return $forkLock
      }
    if $name == 17 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      ashe $zoomValue, $appearance
      return $forkLock
      }
    if $name == 18 {
      $forkLock = 1
      $mirrorLock = false
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      sov $zoomValue, $appearance
      return $forkLock
      }
    if $name == 19 {
      $forkLock = 0
      $mirrorLock = false
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      rthi $zoomValue, $appearance
      return $forkLock
      }
    if $name == 20 {
      $forkLock = 1
      $mirrorLock = false
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      yera $zoomValue, $appearance
      return $forkLock
      }
    if $name == 21 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      eyw $zoomValue
      return $forkLock
      }
    if $name == 22 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      ponwe $zoomValue
      return $forkLock
      }
    if $name == 23 {
      $forkLock = 0
      $mirrorLock = true
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      ken $zoomValue
      return $forkLock
      }
    if $name == 24 {
      $forkLock = 1
      $mirrorLock = false
      iLiner $latitudeView, $zoomValue, $xPoint, $yPoint, $newString
      placeholder $system, $zoomValue, $xPoint, $yPoint, $latitudeView, $fork, $forkLock, $appearance
      aisha $zoomValue, $appearance
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
learn aisha $zoomValue, $appearance {
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
$defaultZoom = 5 # no less then five!!!
$zoomValueT = cryptic 2, $defaultZoom
$shadow = $figure * $zoomValueT
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
#swapped forth page
canvascolor $backgroundR, $backgroundG, $backgroundB
#penwidth 7
pencolor $runeColorR, $runeColorG, $runeColorB
#global_variables_(in_recent_implementation_an_explicit_declaration_
#_______in_functions_(in_parameters_list)_may_be_omitted*_--irulan)
$appearance = true
#cannot make it scalable yet... but i have tried that for only one call
$system = true
$rowHeight = $magic * 3
$switch = 0#*_--irulan_(does_it_make_an_ambiguity_--see_'global_variables'_comment_earlier)_
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
$stringLimit = 12
#$rowLimit = 4
$xSize = ($stringLimit + 1) * $figure * $zoomValueT
$rightMargin = $xSize - round ($figure * 1.732051) #sqrt 3
$ySize = round ($xSize * 1.414214) #sqrt 2
#1 * 
canvassize $xSize, $ySize
fontsize 40
penwidth $zoomValueT
# oyerem [runes]
      $forkLock = 0# dirty global
      $mirrorLock = false
#print "?"
$turns = 0
$frame = 0
#snap 0
repeat 4 {
#         if $turns == 4 { $turns = 0 }
for $scans = 1 to 5 {
repeat 2 {
$name = 0
clear
go 60, 60
print $frame
$frame = $frame + 1
for $row = 0 to 3 {
   $newString = true
   $xPoint = $rightMargin
   $yPoint = ($rowHeight + $rowHeight * $row) * $zoomValueT
#   $columnTrigger = 0
   for $column = 1 to 6 {
      $name = $name + 1
      $zoomScan = cryptic (ringZoom $scans, $column), $defaultZoom
      $forkLock = moan $name, $system, $zoomScan, $xPoint, $yPoint, $space, $newString, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $turns, $appearance
# dead     print $columnTrigger
# dead     print cryptic $columnTrigger, $defaultZoom
#      if $columnTrigger < 4 {
# $columnTrigger = $columnTrigger + 1
# }
      $newString = false
      }
   }
message "say 'Cookie!'" 
if $frame == 37 {snap 2}
         $appearance = not $appearance
         }#repeat 2
   }
         $turns = $turns + 1
         }#repeat 4

exit


reset
spritehide
canvascolor $backgroundR, $backgroundG, $backgroundB
#penwidth 7
pencolor $runeColorR, $runeColorG, $runeColorB
#global_variables_(in_recent_implementation_an_explicit_declaration_
#_______in_functions_(in_parameters_list)_may_be_omitted*_--irulan)
$appearance = true
#cannot make it scalable yet... but i have tried that for only one call
$defaultZoom = 3
$zoomValueT = cryptic 2, $defaultZoom
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
# oyerem [runes]
$newString = true
      $forkLock = 0# dirty global
      $mirrorLock = false
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
aisha $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
argir $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
ashe $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
bessa $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
chawa $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
dawa $zoomValueT
$newString = true
$xPoint = 815
$yPoint = 155 * $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
eyw $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
fehu $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
gad $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
ingif $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
isa $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
iywa $zoomValueT, $appearance
$newString = true
$xPoint = 815
$yPoint = 240 * $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
ken $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
mand $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
naue $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
othir $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
ponwe $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
reith $zoomValueT, $appearance
$newString = true
$xPoint = 815
$yPoint = 325 * $zoomValueT
#$forkIt = 1
#$zoomValueT = cryptic 0, $defaultZoom
#$superScripted = true
#$foreScripted = true
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
rthi $zoomValueT, $appearance
#$zoomValueT = cryptic 0, $defaultZoom
#$forkIt = 1
#$newString = true
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
sov $zoomValueT, $appearance
#$forkIt = 0
# $latitudeView = false
#$zoomValueT = cryptic 1, $defaultZoom
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
thured $zoomValueT
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
uru $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
wunyo $zoomValueT, $appearance
iLiner $latitudeView, $zoomValueT, $xPoint, $yPoint, $newString
placeholder $system, $zoomValueT, $xPoint, $yPoint, $latitudeView, $forkIt, $forkLock, $appearance
yera $zoomValueT, $appearance
#
# thonri oyer [empty rune]
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
$forkIt = 3
$appearance = false
#snap 0 #uncomment 'snaps' in this function's definition for step mode (and comment its own 'waits' out)
faceDancer $entryOfDemo, $name, $system, $zoomValueT, $xPoint, $yPoint, $space, $newString, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $forkIt, $appearance
$entryOfDemo = 1
$xPoint = 415
$yPoint = 405 * $zoomValueT
$name = 20
faceDancer $entryOfDemo, $name, $system, $zoomValueT, $xPoint, $yPoint, $space, $newString, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $forkIt, $appearance
$xPoint = 215
$yPoint = 405 * $zoomValueT
$name = 16
faceDancer $entryOfDemo, $name, $system, $zoomValueT, $xPoint, $yPoint, $space, $newString, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $forkIt, $appearance
$name = 20
faceDancer $entryOfDemo, $name, $system, $zoomValueT, $xPoint, $yPoint, $space, $newString, $cluster, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $forkIt, $appearance
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

---

#### pictures: old font vs new font

old demo script had multiple issues with the font because i was trying to tie glyphs' strokes to some "magic numbers" to make the font looking "cohesive" | now i have moved away from that layout, even though certain combinations of glyphs were looking really chill; here is my new improved font
:-: | :-:
<img width="450" title="old demo script's font" src="https://user-images.githubusercontent.com/98284211/167231096-d6b4b19e-d460-42dd-946e-767da28a84f3.svg" alt="treefingers high contrast A4" /> | <img width="450" alt="treefingers  2_0_3 A4" title="my new improved font" src="https://github.com/user-attachments/assets/6c386da2-fae5-48f0-bec3-773606b9f629" />


