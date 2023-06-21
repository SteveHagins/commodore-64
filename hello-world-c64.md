# "Hello, World!"  in Commodore 64 assembly language:

```assembly
        ; Set up screen and cursor
        lda #$0c        ; Set text color (light blue)
        jsr $ffd2       ; CHROUT
        lda #$00        ; Set background color (black)
        jsr $ffd2       ; CHROUT
        lda #$18        ; Set cursor shape (underline)
        jsr $ffd2       ; CHROUT

        ; Print the message
        ldx #0          ; Start with first character
loop:
        lda message,x   ; Load character from message string
        beq done        ; If end of string, exit
        jsr $ffd2       ; CHROUT
        inx             ; Move to next character
        jmp loop        ; Repeat for the next character

done:
        rts             ; Return from subroutine

message:
        .byte "Hello, World!",0

        ; Start of the program
        org $0801       ; Load address
        word start      ; Starting address

start:
        jsr $e544       ; Clear screen
        jsr $e476       ; Disable RUN/STOP and RESTORE keys
        jsr $e3fd       ; Enable interrupt routine

        jsr main        ; Jump to the main program

        jmp *           ; Infinite loop
```

This program sets up the screen and cursor, then prints the "Hello, World!" message character by character. It uses the `CHROUT` routine to output each character to the screen. The program starts at the label `start` and includes initialization routines for clearing the screen and enabling interrupt handling.

To assemble and run the program on a Commodore 64, you would need an assembler program like Turbo Assembler (TASM) or ACME. Once assembled, you can load and run the program using a Commodore 64 emulator or a real Commodore 64 machine.

Please note that memory locations and specific routines used in this example may vary depending on the assembler and development environment you're using.
