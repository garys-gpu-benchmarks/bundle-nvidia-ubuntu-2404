# NVIDIA CUDA - Ubuntu 24.04 benchmark bundle

All 32 benchmarks for this platform, each pinned to its tested v1.0.1 commit as a git submodule.
Project home: https://github.com/garymichaelbass

```bash
git clone --recurse-submodules https://github.com/garys-gpu-benchmarks/bundle-nvidia-ubuntu-2404.git
cd bundle-nvidia-ubuntu-2404
./run.sh list                # the 32 benchmarks
./run.sh 205                 # smoke run of benchmark 205
./run.sh 205 --baseline      # standard run
./run.sh all                 # all 32, logs in results/
```

Clone without --recurse-submodules to download only what you run: ./run.sh fetches each benchmark on first use.

Do not use Download ZIP: GitHub's ZIP files leave the benchmarks/ folders empty.

## Benchmarks

- **201** - `benchmarks/nvidia-u24-201` - [201-sys-bench-nvidia-cuda-stack-validation-ubu2404](https://github.com/garys-gpu-benchmarks/201-sys-bench-nvidia-cuda-stack-validation-ubu2404)
- **202** - `benchmarks/nvidia-u24-202` - [202-sys-bench-nvidia-gpu-health-validation-ubu2404](https://github.com/garys-gpu-benchmarks/202-sys-bench-nvidia-gpu-health-validation-ubu2404)
- **203** - `benchmarks/nvidia-u24-203` - [203-sys-bench-nvidia-system-stress-stability-ubu2404](https://github.com/garys-gpu-benchmarks/203-sys-bench-nvidia-system-stress-stability-ubu2404)
- **204** - `benchmarks/nvidia-u24-204` - [204-gpu-bench-nvidia-sdc-ecc-integrity-ubu2404](https://github.com/garys-gpu-benchmarks/204-gpu-bench-nvidia-sdc-ecc-integrity-ubu2404)
- **205** - `benchmarks/nvidia-u24-205` - [205-gpu-bench-nvidia-pytorch-tensor-correctness-ubu2404](https://github.com/garys-gpu-benchmarks/205-gpu-bench-nvidia-pytorch-tensor-correctness-ubu2404)
- **206** - `benchmarks/nvidia-u24-206` - [206-sys-bench-nvidia-fio-nvme-sweep-ubu2404](https://github.com/garys-gpu-benchmarks/206-sys-bench-nvidia-fio-nvme-sweep-ubu2404)
- **207** - `benchmarks/nvidia-u24-207` - [207-sys-bench-nvidia-stream-ddr5-bandwidth-ubu2404](https://github.com/garys-gpu-benchmarks/207-sys-bench-nvidia-stream-ddr5-bandwidth-ubu2404)
- **208** - `benchmarks/nvidia-u24-208` - [208-sys-bench-nvidia-iperf3-network-performance-ubu2404](https://github.com/garys-gpu-benchmarks/208-sys-bench-nvidia-iperf3-network-performance-ubu2404)
- **209** - `benchmarks/nvidia-u24-209` - [209-sys-bench-nvidia-multichase-numa-latency-ubu2404](https://github.com/garys-gpu-benchmarks/209-sys-bench-nvidia-multichase-numa-latency-ubu2404)
- **210** - `benchmarks/nvidia-u24-210` - [210-sys-bench-nvidia-numa-cache-performance-ubu2404](https://github.com/garys-gpu-benchmarks/210-sys-bench-nvidia-numa-cache-performance-ubu2404)
- **211** - `benchmarks/nvidia-u24-211` - [211-sys-bench-nvidia-linux-perf-pmu-ubu2404](https://github.com/garys-gpu-benchmarks/211-sys-bench-nvidia-linux-perf-pmu-ubu2404)
- **212** - `benchmarks/nvidia-u24-212` - [212-sys-bench-nvidia-lmbench-microbench-suite-ubu2404](https://github.com/garys-gpu-benchmarks/212-sys-bench-nvidia-lmbench-microbench-suite-ubu2404)
- **213** - `benchmarks/nvidia-u24-213` - [213-sys-bench-nvidia-gups-random-memory-ubu2404](https://github.com/garys-gpu-benchmarks/213-sys-bench-nvidia-gups-random-memory-ubu2404)
- **214** - `benchmarks/nvidia-u24-214` - [214-gpu-bench-nvidia-memcpy-transfer-bandwidth-ubu2404](https://github.com/garys-gpu-benchmarks/214-gpu-bench-nvidia-memcpy-transfer-bandwidth-ubu2404)
- **215** - `benchmarks/nvidia-u24-215` - [215-gpu-bench-nvidia-babelstream-hbm-bandwidth-ubu2404](https://github.com/garys-gpu-benchmarks/215-gpu-bench-nvidia-babelstream-hbm-bandwidth-ubu2404)
- **216** - `benchmarks/nvidia-u24-216` - [216-gpu-bench-nvidia-nccl-bandwidth-test-ubu2404](https://github.com/garys-gpu-benchmarks/216-gpu-bench-nvidia-nccl-bandwidth-test-ubu2404)
- **217** - `benchmarks/nvidia-u24-217` - [217-gpu-bench-nvidia-gemm-cublas-micro-ubu2404](https://github.com/garys-gpu-benchmarks/217-gpu-bench-nvidia-gemm-cublas-micro-ubu2404)
- **218** - `benchmarks/nvidia-u24-218` - [218-gpu-bench-nvidia-cudnn-convolution-micro-ubu2404](https://github.com/garys-gpu-benchmarks/218-gpu-bench-nvidia-cudnn-convolution-micro-ubu2404)
- **219** - `benchmarks/nvidia-u24-219` - [219-gpu-bench-nvidia-torch-micro-suite-ubu2404](https://github.com/garys-gpu-benchmarks/219-gpu-bench-nvidia-torch-micro-suite-ubu2404)
- **220** - `benchmarks/nvidia-u24-220` - [220-gpu-bench-nvidia-linpack-hpl-fp64-ubu2404](https://github.com/garys-gpu-benchmarks/220-gpu-bench-nvidia-linpack-hpl-fp64-ubu2404)
- **221** - `benchmarks/nvidia-u24-221` - [221-gpu-bench-nvidia-resnet50-pytorch-training-ubu2404](https://github.com/garys-gpu-benchmarks/221-gpu-bench-nvidia-resnet50-pytorch-training-ubu2404)
- **222** - `benchmarks/nvidia-u24-222` - [222-gpu-bench-nvidia-resnet50-pytorch-inference-ubu2404](https://github.com/garys-gpu-benchmarks/222-gpu-bench-nvidia-resnet50-pytorch-inference-ubu2404)
- **223** - `benchmarks/nvidia-u24-223` - [223-gpu-bench-nvidia-bert-base-inference-ubu2404](https://github.com/garys-gpu-benchmarks/223-gpu-bench-nvidia-bert-base-inference-ubu2404)
- **224** - `benchmarks/nvidia-u24-224` - [224-gpu-bench-nvidia-sdxl-diffusers-latency-ubu2404](https://github.com/garys-gpu-benchmarks/224-gpu-bench-nvidia-sdxl-diffusers-latency-ubu2404)
- **225** - `benchmarks/nvidia-u24-225` - [225-gpu-bench-nvidia-distilbert-hf-classification-ubu2404](https://github.com/garys-gpu-benchmarks/225-gpu-bench-nvidia-distilbert-hf-classification-ubu2404)
- **226** - `benchmarks/nvidia-u24-226` - [226-gpu-bench-nvidia-jax-xla-forwardpass-ubu2404](https://github.com/garys-gpu-benchmarks/226-gpu-bench-nvidia-jax-xla-forwardpass-ubu2404)
- **227** - `benchmarks/nvidia-u24-227` - [227-gpu-bench-nvidia-vllm-kvcache-stress-ubu2404](https://github.com/garys-gpu-benchmarks/227-gpu-bench-nvidia-vllm-kvcache-stress-ubu2404)
- **228** - `benchmarks/nvidia-u24-228` - [228-gpu-bench-nvidia-vllm-throughput-latency-ubu2404](https://github.com/garys-gpu-benchmarks/228-gpu-bench-nvidia-vllm-throughput-latency-ubu2404)
- **229** - `benchmarks/nvidia-u24-229` - [229-gpu-bench-nvidia-vllm-mistral-cuda-ubu2404](https://github.com/garys-gpu-benchmarks/229-gpu-bench-nvidia-vllm-mistral-cuda-ubu2404)
- **230** - `benchmarks/nvidia-u24-230` - [230-gpu-bench-nvidia-sglang-prompt-response-ubu2404](https://github.com/garys-gpu-benchmarks/230-gpu-bench-nvidia-sglang-prompt-response-ubu2404)
- **231** - `benchmarks/nvidia-u24-231` - [231-gpu-bench-nvidia-sglang-serving-latency-ubu2404](https://github.com/garys-gpu-benchmarks/231-gpu-bench-nvidia-sglang-serving-latency-ubu2404)
- **232** - `benchmarks/nvidia-u24-232` - [232-gpu-bench-nvidia-rag-faiss-end2end-ubu2404](https://github.com/garys-gpu-benchmarks/232-gpu-bench-nvidia-rag-faiss-end2end-ubu2404)
