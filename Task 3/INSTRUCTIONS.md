# RISC-V Assembly Instructions with Encodings

## R-Type (Register-Register Instructions)

| Instruction | Operation | Binary Encoding | Hexadecimal Representation |
|------------|-----------|-----------------|----------------------------|
| `mul a5, a4, a5` | `a5 = a4 * a5` | `0000000 00101 00100 000 00101 0110011` | `0x02F707B3` |
| `mv a0, a5` | `a0 = a5` | `0000000 00000 00101 000 01010 0110011` | `0x00078513` |
| `sltu a5, a0, a5` | `a5 = (a0 < a5) ? 1 : 0 (unsigned)` | `0000000 00101 01010 011 00101 0110011` | `0x00030333` |

## I-Type (Immediate Instructions)

| Instruction | Operation | Binary Encoding | Hexadecimal Representation |
|------------|-----------|-----------------|----------------------------|
| `li a5, 1` | `a5 = 1` | `000001000111 10000 000 00101 0010011` | `0x0004785` |
| `addi sp, sp, -48` | `sp = sp - 48` | `000001110001 11101 000 11101 0010011` | `0x71790000` |
| `lw a5, -20(s0)` | `a5 = *(s0 - 20)` | `111111111100 01000 010 00101 0000011` | `0xFEC42783` |
| `ld a4, -32(s0)` | `a4 = *(s0 - 32)` | `111111110000 01000 011 00100 0000011` | `0xFE043703` |
| `jalr ra, 16(sp)` | `Jump to sp + 16, store return address in ra` | `000000000000 00010 000 00001 1100111` | `0x000080E7` |

## S-Type (Store Instructions)

| Instruction | Operation | Binary Encoding | Hexadecimal Representation |
|------------|-----------|-----------------|----------------------------|
| `sd ra, 40(sp)` | `*(sp + 40) = ra` | `0000000 00001 00010 011 01000 0100011` | `0x00012283` |
| `sw a5, -20(s0)` | `*(s0 - 20) = a5` | `1111111 00101 01000 010 10011 0100011` | `0xFEF42623` |

## B-Type (Branch Instructions)

| Instruction | Operation | Binary Encoding | Hexadecimal Representation |
|------------|-----------|-----------------|----------------------------|
| `bgez a5, 4e` | `Branch to PC + 0x4e if a5 >= 0` | `0 000000 00101 001 01110 0 1100011` | `0x0007DB63` |

## U-Type (Upper Immediate Instructions)

| Instruction | Operation | Binary Encoding | Hexadecimal Representation |
|------------|-----------|-----------------|----------------------------|
| `lui a5, 0x0` | `a5 = 0x0 << 12` | `000000000000 00101 000 0110111` | `0x000007B7` |
| `auipc ra, 0x0` | `ra = PC + (0x0 << 12)` | `000000000000 00001 000 0010111` | `0x00000097` |

## J-Type (Jump Instructions)

| Instruction | Operation | Binary Encoding | Hexadecimal Representation |
|------------|-----------|-----------------|----------------------------|
| `j 70<.L4>` | `Jump to PC + 70` | `1 0100000001 0 0000001000 00000 1101111` | `0xA831` |

## Other Instruction

| Instruction | Operation | Binary Encoding | Hexadecimal Representation |
|------------|-----------|-----------------|----------------------------|
| `addi s0, sp, 48` | `s0 = sp + 48` | `000000000100 00010 000 01000 0010011` | `0x0002A023` |
