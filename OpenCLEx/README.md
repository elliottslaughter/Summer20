# Summer20
OpenCL to spirv example using createProgramWithIL copied from [spirvkernelfromfile](https://github.com/bashbaug/SimpleOpenCLSamples/tree/master/samples/05_spirvkernelfromfile).

## Reproduce On DevCloud
```sh
ssh devcloud
git clone https://github.com/elliottslaughter/Summer20.git
qsub -I -l nodes=1:gpu:ppn=2 -d .
cd Summer20/OpenCLEx
clang -c -cl-std=CL1.2 -target spir64 -emit-llvm -Xclang -finclude-default-header -flto sample_kernel.cl -o sample_kernel64.ll
llvm-spirv sample_kernel64.ll -o sample_kernel64.spv
clang++ -O0 -g -std=c++0x -o main main.cpp -lOpenCL
```
