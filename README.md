# RISC-V Flex (RVflex)
Proposed RISC-V extension for bitwidth-agnostic binaries: Single binary, serves both RV32 and RV64

 * `W`-prefixed instruction (e.g., `ADDW`, `SUBW`, `SLLW`): defined in RV64 for explicit 32-bit operations. Under RVflex, these are treated as regular 32-bit operations on RV32, requiring no special handling. This allows the same binary to use native-width operations via `ADD`/`ADDI` and fixed-width 32-bit operations via W-prefixed instructions on both RV32 and RV64.
 * `LXS`: Load `XLEN`-bit data with scaled index:
   `rd = mem[rs1 + rs2 × sizeof(XLEN)]`
 * `SXS`: Store `XLEN`-bit data with scaled index:
   `mem[rs1 + rs3 × sizeof(XLEN)] = rs2`
 * `ADDS`: Add `XLEN`-scaled register:
   `rd = rs1 + rs2 × sizeof(XLEN)`
 * `ADDSI`: Add `XLEN`-scaled immediate:
   `rd = rs1 + imm × sizeof(XLEN)`
