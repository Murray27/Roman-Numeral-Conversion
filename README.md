# Roman-Numeral-Conversion
This program uses masm to convert numbers 1-9 to roman numeral equivalent. 
.386
.model flat,stdcall
option casemap:none

include     \masm32\include\windows.inc
include     \masm32\include\kernel32.inc
include     \masm32\include\msvcrt.inc

includelib  \masm32\lib\kernel32.lib
includelib  \masm32\lib\msvcrt.lib

.data ; Hold messages to be printed to screen

; Introduction a line of strings will be held in different variables

intro1      db 'The purpose of this program is to convert a number [1 - 9]',13,10,0
intro2      db 'to its Roman Numeral equivalent',13,10,0
intro3      db 'Please enter a number between 1 - 9 to be converted: ',13,10,0

msg1        db '1 is equal to I.',13,10,0
msg2        db '2 is equal to II.',13,10,0
msg3        db '3 is equal to III.',13,10,0
msg4        db '4 is equal to IV.',13,10,0
msg5        db '5 is equal to V.',13,10,0
msg6        db '6 is equal to VI.',13,10,0
msg7        db '7 is equal to VII.',13,10,0
msg8        db '8 is equal to VIII.',13,10,0
msg9        db '9 is equal to IX.',13,10,0
msgend      db 'You pressed %c before hitting RETURN',13,10,0
error       db 'Invalid entry.',13,10,0

.code	; Tell MASM where the code starts

start:	; The CODE entry point to the program

invoke  crt_printf,ADDR intro1
invoke  crt_printf,ADDR intro2 
invoke  crt_printf,ADDR intro3
invoke  crt_getchar ; records the user entry using char

; if statements that will verify input and output result to screen

.if eax == '0'
invoke  crt_printf,ADDR msg1
.elseif eax == '1'
invoke  crt_printf,ADDR msg1
.elseif eax == '2'
invoke  crt_printf,ADDR msg2
.elseif eax == '3'
invoke  crt_printf,ADDR msg3
.elseif eax == '4'
invoke  crt_printf,ADDR msg4
.elseif eax == '5'
invoke  crt_printf,ADDR msg5
.elseif eax == '6'
invoke  crt_printf,ADDR msg6
.elseif eax == '7'
invoke  crt_printf,ADDR msg7
.elseif eax == '8'
invoke  crt_printf,ADDR msg8
.elseif eax == '9'
invoke  crt_printf,ADDR msg9
.else
invoke  crt_printf,ADDR msgend
.endif
    invoke  ExitProcess,0

END start
