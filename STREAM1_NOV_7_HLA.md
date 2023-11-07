# HLA Stdlib

`stdout.put` outputs integers in decimal format
`stdout.put` outputs registers, bytes, words, dwords in hex format
`stdin.get`'s input base is hex for those same 'types', but will expect decimal format if its argument is of an integer type.

If you want to display a value in decimal format but it's stored in a register, use `stdout.puti32` (or ...i16 etc).

If you want to use a decimal base when storing an input to a register, byte, word, etc., use `stdin.geti32` etc.

If you want to use a hex base when storing an input to an integer type, use `stdin.geth32` etc. For output, `stdout.puth32` etc.

# Sign Extension

- `cbw()` = "convert byte in AL to word in AX"
- `cwd()` = "convert word in AX to doubleword in DX:AX"
- `cdq()` = "convert doubleword in EAX to quadword in EDX:EAX"
- `cwde()` = "convert word in AX to doubleword in EAX"
- `movsx(source: memory address OR register, dest: register)` = convert byte/word/doubleword in source to word/doubleword/quadword in dest (dest must be larger than source)
- `movzx(source, dest)` works the same as `movesx` for zero extension
- to zero extend values in 8-bit registers, just zero out their complementary high-order register:
  - AL -> AH, BL -> BH, etc.
