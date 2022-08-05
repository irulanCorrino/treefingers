#### incomplete module [version 2.1]

>```
>#_inheritance 2.1 [corrected version of 1.0]
>#to implement more parameters smoe changes would be needed --irulan
>$v0 = 0
>$v1 = 0
>$v2 = 0
>$v3 = 0
>$v4 = 0
>$v5 = 0
>$v6 = 0
>$v7 = 0
>$v8 = 0
>$v9 = 0
>$v10 = 0
>$v11 = 0
>$v12 = 0
>$v13 = 0
>$v14 = 0
>$v15 = 0
>$v16 = 0
>$v17 = 0
>$v18 = 0
>$v19 = 0
>$v20 = 0
>$v21 = 0
>$v22 = 0
>$v23 = 0
>$v24 = 0
>$v25 = 0
>$v26 = 0
>$v27 = 0
>$v28 = 0
>$v29 = 0
>$v30 = 0
>$v31 = 0
>$v32 = 0
>$v33 = 0
>$v34 = 0
>$v35 = 0
>$v36 = 0
>$v37 = 0
>$v38 = 0
>$v39 = 0
>$v40 = 0
>$v41 = 0
>$v42 = 0
>$v43 = 0
>$v44 = 0
>$v45 = 0
>$v46 = 0
>$v47 = 0
>$v48 = 0
>$v49 = 0
>$v50 = 0
>$v51 = 0
>$v52 = 0
>$v53 = 0
>$v54 = 0
>$v55 = 0
>$v56 = 0
>$v57 = 0
>$v58 = 0
>$v59 = 0
>$v60 = 0
>$v61 = 0
>$v62 = 0
>$v63 = 0
>#_inheritance
>$precedence = 0
>$foreScripted = false
>$afterScripted = false
>$superScripted = false
>$subScripted = false
>#$cluster = false
>#$pattern = 0
>$space = false
>$newline = false
>$fork = 0
>$appearance = false
>$sanity = false
>$first = true # capitalisation rule triggering flag
>$limit = 0
>$spinG = 0
>$hold = false #maybe int
>$identifier = 0
>$pointMe = 0
>$editMode = 0 #maybe int (in‑place & explicit editing)
>learn checkHeirloom $spin, $name, $precedence, $sanity, $limit, $foreScripted, $afterScripted {#to_eliminate_ambiguity
>     if $name == 0 {
>      if $precedence == 4 and ($foreScripted or $afterScripted) {# what are control characters in edit mode? how to exit it?
>       if $foreScripted {
>#       $hold = true #insufficient flag was maybe .$spin is required
>       $foreScripted = false
>       $precedence = 0
>       }
>       else {
>         if $afterScripted {
>          $afterScripted = false
>          $precedence = 0
>          }
>         }# |* poor style oh --irulan (moved between functions) *|
>       }
>       else {
>         if $precedence < 3 { $precedence = $precedence + 1 }
>         }
>      }
>      else {
>        if not $limit and not $sanity {# to switch $sanity at some point
>         if $superScripted { $superScripted = false }
>          else {
>            if $subScripted { $subScripted = false }
>            }
>         }
>         else { $limit = $limit - 1 }# maybe additional thing is needed for safety
>        }
>     }
>#
>learn requestOfInheritance $spin, $name, $foreScripted, $afterScripted, $superScripted, $subScripted, $space, $newline, $precedence, $fork, $appearance, $sanity, $first, $limit {
>     if not $name {#0
>        if $precedence == 1 {# how to exit edit mode?
>         $space = true
>         #$first = true# conditionally
>         }
>         else {#1
>           if $precedence == 2 {
>            $newline = true
>            $space = false
>            #$first = true
>            }
>            else {#2
>               if $precedence == 3 {#
>                $internalName = subcaller 0
>                if $internalName == 24 {
>                 $cursorAction = cursor_stuff 0
>                 while $cursorAction {
>                      
>                      $cursorAction = cursor_stuff 0
>                      }
>                 $precedenceL = 1
>                 $cursorAction = cursor_stuff 1
>                 if $cursorAction {
>                  $precedenceL = 0
>                  while $cursorAction {
>                       
>                       $cursorAction = cursor_stuff 1
>                       }
>                  }
>                  else {
>                    }
>                 
>                 
>                 if $sanity {
>                  }
>                  else {
>                    }
>#                $cursorShift = checkSpin $spinG, false, 1 + checkSpin $spinG, false, 3 + checkSpin $spinG, false, 5 + checkSpin $spinG, false, 7
># cursor stuff $cursor = shiftLeftExplicit (checkSpin $spinG, false, 1), 1 + shiftLeftExplicit (checkSpin $spinG, false, 3), 3 + shiftLeftExplicit (checkSpin $spinG, false, 5), 5 + shiftLeftExplicit (checkSpin $spinG, false, 7), 7
>                 }#24_--hagala
>                 else {#a
>                   if $internalName == 16 {#b
>                    $foreScriptedL = $foreScripted
>                    $afterScriptedL = $afterScripted
>                    $superScriptedL = $superScripted
>                    $subScriptedL = $subScripted
>                    $appearanceL = $appearance
>                    $forkL = $fork
>                    while ($internalName and not (($superScriptedL or $subScriptedL) and ($foreScriptedL or $afterScriptedL))) {#c
>                         $internalName = subcaller 1
>                         #
>                         if $internalName == 15 {
>                          $foreScriptedL = true
>                          if $afterScriptedL { $afterScriptedL = false }
>#
>                          }#15_--raidho
>                          else {#d
>                            if $internalName == 4 {
>                             $afterScriptedL = true
>                             if $foreScriptedL { $foreScriptedL = false }
>#
>                             }#4_--teiwaz
>                            else {#e
>                              if $internalName == 20 {
>                               $superScriptedL = true
>                               if checkSpin $spin, true, 5 {
>                                $limit = 3
>                                $sanity = false
>                                }
>                                else { $limit = 3 - checkSpin $spin, false, 5 }
>                               }#20_--jera
>                               else {#f
>                                 if $internalName == 8 {
>                                  $subScriptedL = true
>                                  if checkSpin $spin, true, 7 {
>                                   $limit = 3
>                                   $sanity = false
>                                   }
>                                   else { $limit = 3 - checkSpin $spin, false, 7 }
>                                  }#8_--algiz
>                                 else {#g
>                                   if $internalName == 0 {
>                                    $editMode = 1
>                                    $precedence == 4
>                                    }
>                                    else {#h
>                                      while $internalName {
>                                           if $internalName == 6 {
>                                            $appearanceL = not $appearanceL
>                                            }#6_--othila
>                                            else {
>                                              if $internalName == 16 {
>                                               $forkL = $forkL + 1
>                                               if $forkL == 4 { $forkL = 0 }
>                                               }#16_--fehu
>                                              }
>                                            #do not forget to make a call to drawing function; beware of global variables
>                                            $internalName = subcaller 2
>                                           }
>                                      }#h
>                                   }#g
>                                 }#f
>                              }#e
>                            }#d
>                         }#c
>                    $foreScripted = $foreScriptedL
>                    $afterScripted = $afterScriptedL
>                    $superScripted = $superScriptedL
>                    $subScripted = $subScriptedL
>                    $appearance = $appearanceL
>                    $fork = $forkL
>                    }#16_--fehu b
>                    else {
>                      if $internalName == 0 {
>                      $editMode = 1
>                      $precedence == 4
>                      }
>                   }#a
>                }#
>              #return 5
>              }#2
>           }#1
>        return 0
>        }#0_--empty
>        else {# |* $name exists *|
>          if $foreScripted {
>           if $superScripted {
>            if checkSpin $spin, true, 1 {
>             $spinG = $spin + shiftLeftExplicit (3 - $limit), 1
>             return 1
>             }
>             else {
>               $spinG = $spin - shiftLeftExplicit (checkSpin $spin, false, 1), 1 + shiftLeftExplicit (3 - $limit), 1
>               return 3
>               }
>            }
>           if $subScripted {
>            if checkSpin $spin, true, 3 {
>             $spinG = $spin + shiftLeftExplicit (3 - $limit), 3
>             return 1
>             }
>             else {
>               $spinG = $spin - shiftLeftExplicit (checkSpin $spin, false, 3), 3 + shiftLeftExplicit (3 - $limit), 3
>               return 3
>               }
>            }
>           }
>           else {
>             if $afterScripted {
>              if $superScripted {
>               if checkSpin $spin, true, 5 {
>                $spinG = $spin + shiftLeftExplicit (3 - $limit), 5
>                return 2
>                }
>                else {
>                  $spinG = $spin - shiftLeftExplicit (checkSpin $spin, false, 5), 5 + shiftLeftExplicit (3 - $limit), 5
>                  return 4
>                  }
>               }
>              if $subScripted {
>               if checkSpin $spin, true, 7 {
>                $spinG = $spin + shiftLeftExplicit (3 - $limit), 7
>                return 2
>                }
>                else {
>                  $spinG = $spin - shiftLeftExplicit (checkSpin $spin, false, 7), 7 + shiftLeftExplicit (3 - $limit), 7
>                  return 4
>                  }
>               }
>              }
>              else {
>                 $spinG = 1 + shiftLeftExplicit $name, 1 + shiftLeftExplicit $identifier, 9
>                }
>             }
>          }
># $internalName = 1
># if $name == 6 and $newline == true { $appearance = true }##6_--othila*
># if $editLineMode {#not 
># if $name == 7 {}#7_--naudiz
># if $name == 13 { }#13_--dagaz
># }
># if $name == 16 and $newline == true { $fork = $fork + 1 }##16_--fehu*
>#*_--a_new_call_is_so_far_a_$name_--irulan
>     }
>learn subcaller $reason {
>     if not $reason { return ask "input: 24 –select a cluster;  16 –select loci; 0 –edit mode" }
>      else {
>         if $reason == 1 { return ask "input a special number(15or4) or a special number(20or8) for setting a locus; or input 6 for setting an appearance or 16 for doing a transform; 0 –edit mode; 00 –exit a cluster" }
>          else {
>            return ask "input 6 for setting an appearance or 16 for doing a transform; 0 –exit transform mode"
>            }
>        }
>     }
>learn check_last $foreScripted, $superScripted {#, $subScripted
>     if $foreScripted {
>      if $superScripted { return 255 }
>       else { return 127 }
>      }
>      else { return 0 }
>     }
>learn checkSpin $spin, $reason, $address {
>     if $reason {
>      if wrapperSR $spin, $address, 2 { return false }
>       else { return true }
>      }
>      else { return wrapperSR $spin, $address, 2 }
>     }
>learn find_shift $spin {
>     return checkSpin $spin, false, 1 + checkSpin $spin, false, 3
>     }
>learn cursor_stuff $reason {
>     if not $reason { return ask "input: 16 –set a cursor at a line; 24 –set a cursor at a cluster; 0 –stop switching through clusters; 00 –exit cursor moving mode" }
>      else {
>         if $reason == 1 { return ask "input (20or8) for moving a cursor [line mode: up or down; clusters: left or right]; 0 –stop switching through clusters; 00 –exit cursor moving mode" }#00 –for insert mode triggering
>          else {
>            if $reason == 2 { return ask "input a special [fore‑/after‑] number(15or4) or a special [super‑/sub‑] number(20or8) for setting a locus" }
>            else { return ask "for selecting minor member: 20 –left or 8 –right; 0 –exit a cluster’s minor member; 00 –exit cursor moving mode" }#to keep the sane limit here (no inserts above that)
>            }
>         }
>     }
>#a cursor moving wraps on a line; no inserts for big cluster members —only a replacement is allowed; $antiligatur switch!!! $hold? ****
># 0 is acceptable once # 0 is acceptable twice
>#learn inheritedLogic $name, $precedence, $space, $newline, $cluster, $pattern, $foreScripted, $afterScripted, $superScripted, $subScripted, $latitudeView, $fork, $appearance {}
>#
>#_renga_
>learn linkIt $flow, $variable {
>if $flow == 0 { $v0 = $variable }
>else {
>if $flow == 1 { $v1 = $variable }
>else {
> if $flow == 2 { $v2 = $variable }
>else {
> if $flow == 3 { $v3 = $variable }
>else {
> if $flow == 4 { $v4 = $variable }
>else {
> if $flow == 5 { $v5 = $variable }
>else {
> if $flow == 6 { $v6 = $variable }
>else {
> if $flow == 7 { $v7 = $variable }
>else {
> if $flow == 8 { $v8 = $variable }
>else {
> if $flow == 9 { $v9 = $variable }
>else {
> if $flow == 10 { $v10 = $variable }
>else {
> if $flow == 11 { $v11 = $variable }
>else {
> if $flow == 12 { $v12 = $variable }
>else {
> if $flow == 13 { $v13 = $variable }
>else {
> if $flow == 14 { $v14 = $variable }
>else {
> if $flow == 15 { $v15 = $variable }
>else {
> if $flow == 16 { $v16 = $variable }
>else {
> if $flow == 17 { $v17 = $variable }
>else {
> if $flow == 18 { $v18 = $variable }
>else {
> if $flow == 19 { $v19 = $variable }
>else {
> if $flow == 20 { $v20 = $variable }
>else {
> if $flow == 21 { $v21 = $variable }
>else {
> if $flow == 22 { $v22 = $variable }
>else {
> if $flow == 23 { $v23 = $variable }
>else {
> if $flow == 24 { $v24 = $variable }
>else {
> if $flow == 25 { $v25 = $variable }
>else {
> if $flow == 26 { $v26 = $variable }
>else {
> if $flow == 27 { $v27 = $variable }
>else {
> if $flow == 28 { $v28 = $variable }
>else {
> if $flow == 29 { $v29 = $variable }
>else {
> if $flow == 30 { $v30 = $variable }
>else {
> if $flow == 31 { $v31 = $variable }
>else {
> if $flow == 32 { $v32 = $variable }
>else {
> if $flow == 33 { $v33 = $variable }
>else {
> if $flow == 34 { $v34 = $variable }
>else {
> if $flow == 35 { $v35 = $variable }
>else {
> if $flow == 36 { $v36 = $variable }
>else {
> if $flow == 37 { $v37 = $variable }
>else {
> if $flow == 38 { $v38 = $variable }
>else {
> if $flow == 39 { $v39 = $variable }
>else {
> if $flow == 40 { $v40 = $variable }
>else {
> if $flow == 41 { $v41 = $variable }
>else {
> if $flow == 42 { $v42 = $variable }
>else {
> if $flow == 43 { $v43 = $variable }
>else {
> if $flow == 44 { $v44 = $variable }
>else {
> if $flow == 45 { $v45 = $variable }
>else {
> if $flow == 46 { $v46 = $variable }
>else {
> if $flow == 47 { $v47 = $variable }
>else {
> if $flow == 48 { $v48 = $variable }
>else {
> if $flow == 49 { $v49 = $variable }
>else {
> if $flow == 50 { $v50 = $variable }
>else {
> if $flow == 51 { $v51 = $variable }
>else {
> if $flow == 52 { $v52 = $variable }
>else {
> if $flow == 53 { $v53 = $variable }
>else {
> if $flow == 54 { $v54 = $variable }
>else {
> if $flow == 55 { $v55 = $variable }
>else {
> if $flow == 56 { $v56 = $variable }
>else {
> if $flow == 57 { $v57 = $variable }
>else {
> if $flow == 58 { $v58 = $variable }
>else {
> if $flow == 59 { $v59 = $variable }
>else {
> if $flow == 60 { $v60 = $variable }
>else {
> if $flow == 61 { $v61 = $variable }
>else {
> if $flow == 62 { $v62 = $variable }
>else {
> if $flow == 63 { $v63 = $variable }
> }
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>  }
>#_glacierMirror
>learn glacierMirror $flow, $entity {#_*r |* [*renga]? *|
>      linkIt $flow, $entity
>      $flow = $flow + 1
>     if $flow == 62 { message "memory is low" }
>     }
>learn wrapperSR $value, $address, $dLenght {
>     if $value {
>      $firstOperand = shiftRightExplicit $value, $address
>      $addressShifted = $address + $dLenght
>      $secondOperand = shiftRightExplicit $value, $addressShifted
>      $result = $firstOperand - $secondOperand * (2 ^ $dLenght)
>      return $result
>      }
>      else { return 0 }
>     }
>learn shiftRightExplicit $value, $address {
>     $c = $value
>     repeat $address {
>           $oddity = mod $c, 2
>           if not $oddity { $c = $c / 2 }
>            else { $c = ($c - 1) / 2 }
>           }
>     return $c
>     }
>#learn containerSR { # |* this stuff uses globals so it will not work in a practical application --irulan *| no no the stuff is not using globals [was disappointed by other things really abusing globals (checkSpin)]
># $value = 11264
># $address = 10
># $dLenght = 2
># return wrapperSR $value, $address, $dLenght
># } 
>#learn containerSR {#alternative function if one is unfamiliar with addressing
># $value = 11
># $address = 0
># $dLenght = 2
># return wrapperSR $value, $address, $dLenght
># }
>##_SRCounter_function
>learn shiftRight $value, $power {
>       $c = 1
>       $d = $value
>       while $d > 2 {
>            $c = $c + 1
>            $d = $d / 2
>            }
>       $power = $c
>       }
>learn shiftLeftExplicit $value, $address {
>     $d = $value
>     repeat $address {
>           $d = $d * 2
>           }
>     return $d
>     }
>#snippet_test_code:
>#reset
>#penup
>#forward 12
>#print containerSR
>#forward 12
>#
># |* to make this table for a 32bit field *|
>#65536_--16_________________________________&&_--131071
>#32768_--15____&&_--65535_(sixteen_bits)_
>#16384_--14____&&_--32767
>#8192_--13____&&_--16383
>#4096_--12____&&_--8191
>#2048_--11____&&_--4095
>#1024_--10____&&_--2047
>#512_--9____&&_--1023
>#256_--8____&&_--511
>#128_--7____&&_--255
>#64_--6____&&_--127
>#32_--5____&&_--63
>#16_--4____&&_--31
>#8_--3____&&_--15
>#4_--2____&&_--7
>#2_--1____&&_--3
>#1_--0____&&_--1
>#_0_--null
>learn leadMe $flow {#that could be done more transparently |* oh... did i mean back then that 'if $condition {}' used as 'switch $condition {case here}' is better than nested stuff 'if $condition {} else {if $condition {}else {if $condition {}}}'? --irulan *|
>if $flow == 0 { return $v0 }
>else {
>if $flow == 1 { return $v1 }
>else {
> if $flow == 2 { return $v2 }
>else {
> if $flow == 3 { return $v3 }
>else {
> if $flow == 4 { return $v4 }
>else {
> if $flow == 5 { return $v5 }
>else {
> if $flow == 6 { return $v6 }
>else {
> if $flow == 7 { return $v7 }
>else {
> if $flow == 8 { return $v8 }
>else {
> if $flow == 9 { return $v9 }
>else {
> if $flow == 10 { return $v10 }
>else {
> if $flow == 11 { return $v11 }
>else {
> if $flow == 12 { return $v12 }
>else {
> if $flow == 13 { return $v13 }
>else {
> if $flow == 14 { return $v14 }
>else {
> if $flow == 15 { return $v15 }
>else {
> if $flow == 16 { return $v16 }
>else {
> if $flow == 17 { return $v17 }
>else {
> if $flow == 18 { return $v18 }
>else {
> if $flow == 19 { return $v19 }
>else {
> if $flow == 20 { return $v20 }
>else {
> if $flow == 21 { return $v21 }
>else {
> if $flow == 22 { return $v22 }
>else {
> if $flow == 23 { return $v23 }
>else {
> if $flow == 24 { return $v24 }
>else {
> if $flow == 25 { return $v25 }
>else {
> if $flow == 26 { return $v26 }
>else {
> if $flow == 27 { return $v27 }
>else {
> if $flow == 28 { return $v28 }
>else {
> if $flow == 29 { return $v29 }
>else {
> if $flow == 30 { return $v30 }
>else {
> if $flow == 31 { return $v31 }
>else {
> if $flow == 32 { return $v32 }
>else {
> if $flow == 33 { return $v33 }
>else {
> if $flow == 34 { return $v34 }
>else {
> if $flow == 35 { return $v35 }
>else {
> if $flow == 36 { return $v36 }
>else {
> if $flow == 37 { return $v37 }
>else {
> if $flow == 38 { return $v38 }
>else {
> if $flow == 39 { return $v39 }
>else {
> if $flow == 40 { return $v40 }
>else {
> if $flow == 41 { return $v41 }
>else {
> if $flow == 42 { return $v42 }
>else {
> if $flow == 43 { return $v43 }
>else {
> if $flow == 44 { return $v44 }
>else {
> if $flow == 45 { return $v45 }
>else {
> if $flow == 46 { return $v46 }
>else {
> if $flow == 47 { return $v47 }
>else {
> if $flow == 48 { return $v48 }
>else {
> if $flow == 49 { return $v49 }
>else {
> if $flow == 50 { return $v50 }
>else {
> if $flow == 51 { return $v51 }
>else {
> if $flow == 52 { return $v52 }
>else {
> if $flow == 53 { return $v53 }
>else {
> if $flow == 54 { return $v54 }
>else {
> if $flow == 55 { return $v55 }
>else {
> if $flow == 56 { return $v56 }
>else {
> if $flow == 57 { return $v57 }
>else {
> if $flow == 58 { return $v58 }
>else {
> if $flow == 59 { return $v59 }
>else {
> if $flow == 60 { return $v60 }
>else {
> if $flow == 61 { return $v61 }
>else {
> if $flow == 62 { return $v62 }
>else {
> if $flow == 63 { return $v63 }
> }
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>}
>     }
>learn void_test {
>     clear
>     center
>     direction 0
>     forward 200
>     print "$name is equal to " + $name
>     direction 180
>     forward 10
>     if $foreScripted {
>        direction 0
>        print "foreScripted is equal to true"
>        direction 180
>        forward 10
>        }
>     if $afterScripted {
>        direction 0
>        print "afterScripted is equal to true"
>        direction 180
>        forward 10
>        }
>     if $superScripted {
>        direction 0
>        print "superScripted is equal to true"
>        direction 180
>        forward 10
>        }
>     if $subScripted {
>        direction 0
>        print "subScripted is equal to true"
>        direction 180
>        forward 10
>        }
>     if $space {
>        direction 0
>        print "space is equal to true"
>        direction 180
>        forward 10
>        }
>     if $newline {
>        direction 0
>        print "newline is equal to true"
>        direction 180
>        forward 10
>        }
>     if $precedence {
>        direction 0
>        print "precedence is equal to " + $precedence
>        direction 180
>        forward 10
>        }
>     if $fork {
>        direction 0
>        print "fork is equal to " + $fork
>        direction 180
>        forward 10
>        }
>     if $hold {
>        direction 0
>        print "$hold is equal to true"
>        direction 180
>        forward 10
>        }
>     if $editMode {
>        direction 0
>        print "editMode is equal to true"
>        direction 180
>        forward 10
>        }
>     direction 0
>     print "first is equal to " + $first
>     direction 180
>     forward 10
>     direction 0
>     print "limit is equal to " + $limit
>     direction 180
>     forward 10
>     direction 0
>     print "sanity is equal to " + $sanity
># if $cluster {
># direction 0
># print "cluster is equal to " + $cluster
># direction 180
># forward 10
># }
>     if $name {
>        direction 180
>        forward 10
>        direction 0
>        if $appearance { print "entity is mirrored" }
>         else { print "default appearance" }
>        direction 180
>        forward 10
>        }
>     center
>     direction 180
>     forward 20
>     test_spinG spinG, $identifier
>     }
>#
>#_test
>reset
>fontsize 10
>spritehide
>penup
>$condition = true
>$flow = 0
>$input = ""
>$name = 0#difference($flow - 1)
>while ($condition == true) {
>     if $flow != 64 {
>      $ask = -1
>      while $ask == -1 {
>           $ask = ask "input number in range from 0 to 24"
>           if not ($ask >=0 and $ask <= 24) { $ask = -1 }
>            else { $name = $ask }
>           }
>      checkHeirloom $spinG, $name, $precedence, $sanity, $limit, $foreScripted, $afterScripted#, $cluster
>      $action = requestOfInheritance $spinG, $name, $foreScripted, $afterScripted, $superScripted, $subScripted, $space, $newline, $precedence, $fork, $appearance, $sanity, $first, $limit
>      if $action { 
>       if $action == 1 { glacierMirror $flow, $spinG }
>        else {
>          if $action == 2 {
>           $swap = $flow
>           $nameSwap = leadMe $flow
>           $flow = $flow - checkSpin $spinG, false, 1 - checkSpin $spinG, false, 3 - checkSpin $spinG, false, 5 - checkSpin $spinG, false, 7 #dumb misdirection
>           linkIt $flow, $spinG
>           $flow = $swap
>           glacierMirror $flow, $nameSwap
>           }
>           else {
>             if $action == 3 {
>              }
>              else {
>                if $action == 4 {
>                 }
>                 else {
>                   if $action == 5 {
>                    }
>                    else {
>                      if $action == 6 {}
>                      }
>                   }
>                }
>
>find_shift $spinG
>             }
>          }
>       }
>       else {}#probably
>      void_test
>      $input = ask "to stop say 'stop'"
>      if $input == "stop" { $condition = false }
>      }
>      else {
>        message "overflow"
>        $condition = false
>        }
>     $last = check_last $foreScripted, $superScripted
>     }
>spriteshow
>exit
>
>(checkSpin $spinG, true, 1 and checkSpin $spinG, true, 3 and checkSpin $spinG, true, 5 and checkSpin $spinG, true, 7)
>
>$cursor = shiftLeftExplicit (checkSpin $spinG, false, 1), 1 + shiftLeftExplicit (checkSpin $spinG, false, 3), 3 + shiftLeftExplicit (checkSpin $spinG, false, 5), 5 + shiftLeftExplicit (checkSpin $spinG, false, 7), 7
>
>$cursorShift = checkSpin $spinG, false, 1 + checkSpin $spinG, false, 3 + checkSpin $spinG, false, 5 + checkSpin $spinG, false, 7
>
>to get it properly pointed to big member position while it is placed at small cluster members’ loci visually
>*to remember six points:
>                       $beforeUnknown
>                       $inputPenult
>                       $inputAfterEdit
>                       $editedFirst
>                       $editedPenult
>                       $editedLast
>           and to store all four [edited/input minor member] positions for all these [pointed big members of] clusters (24 positions)
>
>
>
>
># if ($precedence == 4) or ($precedence == 5) { $cluster = true }, $cluster
># return $precedence
>
>
>if $precedence == 3 or $precedence == 4 or $precedence == 5 {
>         if $name == 8 {
>          if checkSpin $spin, true, 3 {
>           $sanity = false
>           $limit = 3
>           $name = 0
>           $precedence = 0
>           $subScripted = true
>           }
>           else { $limit = 3 - checkSpin $spin, false, 3 }#to check reaction to an overflow --irulan
>          }
>          else {
>            if checkSpin $spin, true, 1 {
>             $sanity = false
>             $limit = 3
>             $precedence = 0
>             $superScripted = true
>             }
>             else { $limit = 3 - checkSpin $spin, false, 1 }
>            }
>         }#poor style oh .now fixing --irulan (moved between functions)#
>         else {
>           if $precedence == 6 {}
>           }
>
>        if not $sanity {# ************************* 'still‑in' flag
>         $sanity = true
>         if $first { $first = false }
>         if $hold { $hold = false }
>         }
>
>
>
># 
># if not $editLineMode and $name and $bundleLenght {# { $editMode = true }
># }
>#
>
>                      $space = false
>                      $newline = true
>                      }# end of a hole in a code
>                      else {#5
>                        if $precedence == 6 {
>#
>#                         if not $first and not $hold {
>#                          $foreScripted = false
>#                          $newline = false
>#                          }
>                           }#6
>
>
>
>
>#learn inheritedProperties $precedence, $foreScripted, $afterScripted, $superScripted, $subScripted, $space, $newline, $fork, $appearance {}
>#
>#learn clusterInheritance $pattern, $precedence {}
>#
>
>
>
>                $foreScripted = true
>                $newline = false
>                }#
>                else {#3
>                  if $precedence == 4 {
>                   $afterScripted = true
>                   $foreScripted = false
>                   }
>                   else {#4
>                     if $precedence == 4 and ($foreScripted or $afterScripted) {
>
>                         #else {#5
>                        #}#5
>                     }#4
>                  }#3
>
>
>                           if $precedence == 1 and ($foreScripted or $afterScripted) {#*
>                            $internalName = subcaller true#
>                            $precedence = 0
>ccl dir 180 fw 10 dir 0 print "branch 1" wait 4
>                            if $internalName == 20 {
>                             $superScripted = true
>                             if $foreScripted {
>                              if checkSpin $spin, true, 1 {
>                               $sanity = false
>                               $limit = 3
>                               }
>                               else { $limit = 3 - checkSpin $spin, false, 1 }
>                              }
>                              else {
>                                if checkSpin $spin, true, 5 {
>                                 $sanity = false
>                                 $limit = 3
>                                 }
>                                 else { $limit = 3 - checkSpin $spin, false, 5 }
>                                }
>                             }#20_--jera
>                             else {
>                               if $internalName == 8 {
>                                $subScripted = true
>                                if $foreScripted {
>                                 if checkSpin $spin, true, 3 {
>                                  $sanity = false
>                                  $limit = 3
>                                  }
>                                  else { $limit = 3 - checkSpin $spin, false, 3 }
>                                 }
>                                 else {
>                                   if checkSpin $spin, true, 7 {
>                                    $sanity = false
>                                    $limit = 3
>                                    }
>                                    else { $limit = 3 - checkSpin $spin, false, 7 }
>                                   }
>                                }#8_--algiz and $afterScripted
>                                else {
>                                  if $sanity {#* i guess is wrong or insufficient; fixed --irulan
>                                   $appearanceL = $appearance
>                                   $forkL = $fork
>                                   while $internalName {
>                                        if $internalName == 6 {
>                                         $appearanceL = not $appearanceL
>                                         }#6_--othila
>                                         else {
>                                           if $internalName == 16 {
>                                            $forkL = $forkL + 1
>                                            if $forkL == 4 { $forkL = 0 }
>                                            }#16_--fehu
>                                           }
>                                        $internalName = subcaller false
>                                        }#|* moved it into loop *|
>                                          #do not forget to make a call to drawing function; beware of global variables |* and i missed $spin in checkSpin $spin, back then... oh --irulan [learn checkSpin [$spin,[?]] $reason, $address {}] *| maybe it was usable without that but a readability is improved
>                                   $appearance = $appearanceL
>                                   $fork = $forkL
>                                   return 6
>                                   }#
>                                  }#
>                               }
>                            }
>#
>
>#                         if $internalName { $precedence = 1 } # maybe is a hole in a head
>
>
>
>
>
>
>
>```
