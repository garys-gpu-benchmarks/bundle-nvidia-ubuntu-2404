# NVIDIA CUDA - Ubuntu 24.04 benchmark bundle

32 system and GPU benchmarks for NVIDIA GPU machines running Ubuntu 24.04,
each pinned to its tested v1.0.9 release.

Use this bundle only on that platform. The others have their own bundle:
[AMD 24.04](https://github.com/garys-gpu-benchmarks/bundle-amd-ubuntu-2404) ·
[NVIDIA 24.04](https://github.com/garys-gpu-benchmarks/bundle-nvidia-ubuntu-2404) ·
[AMD 26.04](https://github.com/garys-gpu-benchmarks/bundle-amd-ubuntu-2604) ·
[NVIDIA 26.04](https://github.com/garys-gpu-benchmarks/bundle-nvidia-ubuntu-2604)

## Before you start

- A freshly installed **Ubuntu 24.04** machine with NVIDIA GPUs, connected to the internet.
- **root** access: log in as root, or run `sudo -i` first.
- Plenty of free disk space. Each benchmark installs its own software the first
  time it runs, and checks for at least 20 GiB free before it does. The AI
  benchmarks also download models.
- For the AI model benchmarks (223 to 231): if a model's license on Hugging
  Face requires it, accept the license there and set a token first:
  `export HF_TOKEN=hf_...`

## Install

```bash
apt-get update && apt-get install -y git tmux
git clone --recurse-submodules https://github.com/garys-gpu-benchmarks/bundle-nvidia-ubuntu-2404 /opt/benchmarks
cd /opt/benchmarks
./run.sh list
```

`./run.sh list` should show all 32 benchmarks as `ready`.
Do not use GitHub's **Download ZIP**: it leaves the benchmark folders empty.

## Getting started: three quick benchmarks

```bash
cd /opt/benchmarks
./run_benchmark_suite.sh -w 201,202,215 -p smoke
```

This runs the short `smoke` profile of three benchmarks:

| Benchmark | What it checks |
|---|---|
| 201 | the GPU software stack is installed and working |
| 202 | GPU health |
| 215 | GPU memory (HBM) bandwidth |

The first run takes much longer than later ones: it installs the NVIDIA driver and CUDA and each
benchmark's software. The install may restart the machine once. If it does,
log in again after the restart, wait a few minutes for setup to finish on its
own, and run the same command again.

Each run prints a short block, and the suite ends with a pass/fail summary.
The full output is in `/opt/benchmarks/benchmark_suite_log/`.

To run a single benchmark with its output on screen:

```bash
./run.sh 205                # setup, then the smoke profile of benchmark 205
./run.sh 205 --baseline     # the standard profile
```

## Run everything

Run the full suite inside `tmux`, so it keeps running if your connection drops.
It takes many hours.

```bash
tmux new -s bench
cd /opt/benchmarks
./run_benchmark_suite.sh
```

This runs all 32 benchmarks with the `smoke` profile, then all with
`baseline`, then all with `extended`. Detach with **Ctrl+B** then **D**;
reattach later with `tmux attach -t bench`.

Run "Getting started" first on a new machine, so the one-time install (and any
restart) happens before the long run.

| Option | What it does |
|---|---|
| `-p smoke` | profiles to run, in order (`smoke`, `baseline`, `extended`; comma-separated) |
| `-w 201,207,221` | only these benchmarks; ranges work too: `-w 201-210` |
| `-r 20` | repeat the whole set 20 times (soak test) |
| `--fail-fast` | stop at the first failed run |
| `-n` | show what would run, without running it |
| `--help` | all options |

## Results

| What | Where |
|---|---|
| Summary of the suite | end of the screen output |
| Full output of every run | `/opt/benchmarks/benchmark_suite_log/` |
| Each benchmark's results | `/opt/benchmarks/<benchmark>/results/` (`raw/` and `parsed/`) |
| One line per run (time, exit code) | `/var/opt/benchmarks/runtime_ledger.csv` |

To copy everything to a Windows laptop, use `get_remote_info.sh` from
[gpu-bench-suite](https://github.com/garys-gpu-benchmarks/gpu-bench-suite).

## Update to a newer release

```bash
cd /opt/benchmarks
git pull && git submodule update --init --recursive
```

Copies made before v1.0.5 keep their benchmarks in a `benchmarks/` subfolder;
delete those and clone again as shown under Install.

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

