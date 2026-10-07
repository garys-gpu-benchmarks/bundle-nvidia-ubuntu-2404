# NVIDIA CUDA - Ubuntu 24.04 benchmark bundle

All 32 benchmarks for this platform, each pinned to its tested v1.0.5 commit as a git submodule.
Project home: https://github.com/garymichaelbass

## Install

On a fresh Ubuntu machine, this downloads all 32 benchmarks into /opt/benchmarks:

```bash
git clone --recurse-submodules https://github.com/garys-gpu-benchmarks/bundle-nvidia-ubuntu-2404 /opt/benchmarks
```

As a normal user (not root), first install git and create the folder:

```bash
sudo apt-get update && sudo apt-get install -y git
sudo mkdir -p /opt/benchmarks && sudo chown "$USER":"$USER" /opt/benchmarks
git clone --recurse-submodules https://github.com/garys-gpu-benchmarks/bundle-nvidia-ubuntu-2404 /opt/benchmarks
```

Each benchmark is then in its own folder, for example /opt/benchmarks/201-…, next to run.sh and run_benchmark_suite.sh. Check with:

```bash
cd /opt/benchmarks && ./run.sh list
```

`./run.sh list` should show all 32 benchmarks as `ready`. To download only the benchmarks you run, leave out `--recurse-submodules`: `./run.sh` then fetches each benchmark the first time it is used.

Do not use Download ZIP: GitHub's ZIP files leave the benchmark folders empty.

## Run

```bash
cd /opt/benchmarks
./run.sh 205                 # setup, then a smoke run of benchmark 205
./run.sh 205 --baseline      # standard run
./run.sh all                 # all 32, logs in results/
```

The first benchmark's setup may install the GPU software stack, ask for your sudo password, and need a reboot. Read each benchmark's README.md before running it.

## Run the whole suite

`run_benchmark_suite.sh` runs every installed benchmark with each profile (smoke, then baseline, then extended), prints one short block per run, keeps the full output in a log file, and ends with a pass/fail summary.

```bash
cd /opt/benchmarks
./run_benchmark_suite.sh                         # all 32 benchmarks, smoke + baseline + extended
./run_benchmark_suite.sh -p smoke                # quick check of everything
./run_benchmark_suite.sh -w 201,207,221 -p baseline  # chosen benchmarks only
./run_benchmark_suite.sh -r 20                   # repeat the whole set 20 times
./run_benchmark_suite.sh --help                  # all options
```

## Update

```bash
cd /opt/benchmarks
git pull && git submodule update --init --recursive
```

If your copy keeps its benchmarks in a benchmarks/ subfolder (bundles published before v1.0.5), delete it and clone again instead, as shown under Install.

## Benchmarks

- **201** - [201-sys-bench-nvidia-cuda-stack-validation-ubu2404](https://github.com/garys-gpu-benchmarks/201-sys-bench-nvidia-cuda-stack-validation-ubu2404)
- **202** - [202-sys-bench-nvidia-gpu-health-validation-ubu2404](https://github.com/garys-gpu-benchmarks/202-sys-bench-nvidia-gpu-health-validation-ubu2404)
- **203** - [203-sys-bench-nvidia-system-stress-stability-ubu2404](https://github.com/garys-gpu-benchmarks/203-sys-bench-nvidia-system-stress-stability-ubu2404)
- **204** - [204-gpu-bench-nvidia-sdc-ecc-integrity-ubu2404](https://github.com/garys-gpu-benchmarks/204-gpu-bench-nvidia-sdc-ecc-integrity-ubu2404)
- **205** - [205-gpu-bench-nvidia-pytorch-tensor-correctness-ubu2404](https://github.com/garys-gpu-benchmarks/205-gpu-bench-nvidia-pytorch-tensor-correctness-ubu2404)
- **206** - [206-sys-bench-nvidia-fio-nvme-sweep-ubu2404](https://github.com/garys-gpu-benchmarks/206-sys-bench-nvidia-fio-nvme-sweep-ubu2404)
- **207** - [207-sys-bench-nvidia-stream-ddr5-bandwidth-ubu2404](https://github.com/garys-gpu-benchmarks/207-sys-bench-nvidia-stream-ddr5-bandwidth-ubu2404)
- **208** - [208-sys-bench-nvidia-iperf3-network-performance-ubu2404](https://github.com/garys-gpu-benchmarks/208-sys-bench-nvidia-iperf3-network-performance-ubu2404)
- **209** - [209-sys-bench-nvidia-multichase-numa-latency-ubu2404](https://github.com/garys-gpu-benchmarks/209-sys-bench-nvidia-multichase-numa-latency-ubu2404)
- **210** - [210-sys-bench-nvidia-numa-cache-performance-ubu2404](https://github.com/garys-gpu-benchmarks/210-sys-bench-nvidia-numa-cache-performance-ubu2404)
- **211** - [211-sys-bench-nvidia-linux-perf-pmu-ubu2404](https://github.com/garys-gpu-benchmarks/211-sys-bench-nvidia-linux-perf-pmu-ubu2404)
- **212** - [212-sys-bench-nvidia-lmbench-microbench-suite-ubu2404](https://github.com/garys-gpu-benchmarks/212-sys-bench-nvidia-lmbench-microbench-suite-ubu2404)
- **213** - [213-sys-bench-nvidia-gups-random-memory-ubu2404](https://github.com/garys-gpu-benchmarks/213-sys-bench-nvidia-gups-random-memory-ubu2404)
- **214** - [214-gpu-bench-nvidia-memcpy-transfer-bandwidth-ubu2404](https://github.com/garys-gpu-benchmarks/214-gpu-bench-nvidia-memcpy-transfer-bandwidth-ubu2404)
- **215** - [215-gpu-bench-nvidia-babelstream-hbm-bandwidth-ubu2404](https://github.com/garys-gpu-benchmarks/215-gpu-bench-nvidia-babelstream-hbm-bandwidth-ubu2404)
- **216** - [216-gpu-bench-nvidia-nccl-bandwidth-test-ubu2404](https://github.com/garys-gpu-benchmarks/216-gpu-bench-nvidia-nccl-bandwidth-test-ubu2404)
- **217** - [217-gpu-bench-nvidia-gemm-cublas-micro-ubu2404](https://github.com/garys-gpu-benchmarks/217-gpu-bench-nvidia-gemm-cublas-micro-ubu2404)
- **218** - [218-gpu-bench-nvidia-cudnn-convolution-micro-ubu2404](https://github.com/garys-gpu-benchmarks/218-gpu-bench-nvidia-cudnn-convolution-micro-ubu2404)
- **219** - [219-gpu-bench-nvidia-torch-micro-suite-ubu2404](https://github.com/garys-gpu-benchmarks/219-gpu-bench-nvidia-torch-micro-suite-ubu2404)
- **220** - [220-gpu-bench-nvidia-linpack-hpl-fp64-ubu2404](https://github.com/garys-gpu-benchmarks/220-gpu-bench-nvidia-linpack-hpl-fp64-ubu2404)
- **221** - [221-gpu-bench-nvidia-resnet50-pytorch-training-ubu2404](https://github.com/garys-gpu-benchmarks/221-gpu-bench-nvidia-resnet50-pytorch-training-ubu2404)
- **222** - [222-gpu-bench-nvidia-resnet50-pytorch-inference-ubu2404](https://github.com/garys-gpu-benchmarks/222-gpu-bench-nvidia-resnet50-pytorch-inference-ubu2404)
- **223** - [223-gpu-bench-nvidia-bert-base-inference-ubu2404](https://github.com/garys-gpu-benchmarks/223-gpu-bench-nvidia-bert-base-inference-ubu2404)
- **224** - [224-gpu-bench-nvidia-sdxl-diffusers-latency-ubu2404](https://github.com/garys-gpu-benchmarks/224-gpu-bench-nvidia-sdxl-diffusers-latency-ubu2404)
- **225** - [225-gpu-bench-nvidia-distilbert-hf-classification-ubu2404](https://github.com/garys-gpu-benchmarks/225-gpu-bench-nvidia-distilbert-hf-classification-ubu2404)
- **226** - [226-gpu-bench-nvidia-jax-xla-forwardpass-ubu2404](https://github.com/garys-gpu-benchmarks/226-gpu-bench-nvidia-jax-xla-forwardpass-ubu2404)
- **227** - [227-gpu-bench-nvidia-vllm-kvcache-stress-ubu2404](https://github.com/garys-gpu-benchmarks/227-gpu-bench-nvidia-vllm-kvcache-stress-ubu2404)
- **228** - [228-gpu-bench-nvidia-vllm-throughput-latency-ubu2404](https://github.com/garys-gpu-benchmarks/228-gpu-bench-nvidia-vllm-throughput-latency-ubu2404)
- **229** - [229-gpu-bench-nvidia-vllm-mistral-cuda-ubu2404](https://github.com/garys-gpu-benchmarks/229-gpu-bench-nvidia-vllm-mistral-cuda-ubu2404)
- **230** - [230-gpu-bench-nvidia-sglang-prompt-response-ubu2404](https://github.com/garys-gpu-benchmarks/230-gpu-bench-nvidia-sglang-prompt-response-ubu2404)
- **231** - [231-gpu-bench-nvidia-sglang-serving-latency-ubu2404](https://github.com/garys-gpu-benchmarks/231-gpu-bench-nvidia-sglang-serving-latency-ubu2404)
- **232** - [232-gpu-bench-nvidia-rag-faiss-end2end-ubu2404](https://github.com/garys-gpu-benchmarks/232-gpu-bench-nvidia-rag-faiss-end2end-ubu2404)

