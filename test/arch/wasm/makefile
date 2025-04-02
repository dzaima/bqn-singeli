SHELL=/usr/bin/env bash -o pipefail

WASI_CLANG = wasi-clang
WASMTIME = wasmtime

default: run-select-shuffle

select-shuffle.bin: select-shuffle.singeli
	@../../../singeli -os stderr -a wasm32,simd128 $< > $@.c
	@$(WASI_CLANG) -msimd128 $@.c -o $@

run-select-shuffle: select-shuffle.bin
	@$(WASMTIME) ./select-shuffle.bin

clean:
	rm *.bin*