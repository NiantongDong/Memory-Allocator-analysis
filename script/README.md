# Memory-Allocator-analysis

## Benchmark setup

We use the benchmark from <https://github.com/daanx/mimalloc-bench>
To gain all the benchmark and memeory allocator codes, run the command

```bash
./build-bench-env.sh all
```

Once the building process completed and succeeded. You will see two new folder `out`  and `external`. The `out` folder will have all the results named by `benchmarkName-threadCount` and the `external` will have any other benchmarks which are not include in the `bench` folder.

The most comman errors for the building process is missing certain packages. Generally the script will install them automatically but some of them may require `sudo` password or `sudo apt-get install`. You can do that manually but we don't have any installation permission problem on MOC.

After that , run the following command to start running the benchmark and allocator

```bash
cd out/bench
../../bench.sh --procs= threadCound allocatorName benchmarkName
```

For example, if we want to run the expresso for system allocator, jemalloc with 1 thread, we can have

```bash

../../bench.sh --procs= 1 sys je expresso

```

To learn more, run the help function to have all the support benchmarks and allocators

```bash

../../bench.sh -h

```

It is also easy to add any new benchmarks and allocators to it. Download the source code to the folder and add the path to `bench.sh`. You can find a section called `The allocator library paths` to add the new allocator to the path and, for benchmark, add the command and paths to the `run test` funtion to support a new benchmark. You may also customize your own input by editing the script. For example, the default value for cfrac benchmark is  17545186520507317056371138836327483792789528, but you can change the value in line 527.

In general, this scipt is developed by dannx and it is a quite powerful and easy-to-use script. 