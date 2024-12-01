# Relu

## 0x00 说明

包含以下内容：

- [X] relu_f32_kernel
- [X] relu_f32x4_kernel(float4向量化版本)
- [X] relu_f16_kernel(fp16版本)
- [X] relu_f16x2_kernel(fp16向量化版本)
- [X] relu_f16x8_kernel(fp16向量化版本)
- [X] relu_f16x8_pack_kernel(fp16向量化，pack版本)
- [X] PyTorch bindings


## 测试

```bash
# 只测试Ada架构 不指定默认编译所有架构 耗时较长: Volta, Ampere, Ada, Hopper, ...
export TORCH_CUDA_ARCH_LIST=Ada 
python3 relu.py
```

输出:

```bash
-------------------------------------------------------------------------------------
                                        S=1024, K=1024
           out_f32: ['0.0         ', '0.0         '], time:0.00527740ms
         out_f32x4: ['0.0         ', '0.0         '], time:0.00370884ms
        out_f32_th: ['0.0         ', '0.0         '], time:0.00778055ms
-------------------------------------------------------------------------------------
           out_f16: ['0.0         ', '0.0         '], time:0.00498462ms
         out_f16x2: ['0.0         ', '0.0         '], time:0.00357628ms
         out_f16x8: ['0.0         ', '0.0         '], time:0.00371480ms
     out_f16x8pack: ['0.0         ', '0.0         '], time:0.00370741ms
        out_f16_th: ['0.0         ', '0.0         '], time:0.00782657ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=1024, K=2048
           out_f32: ['0.27619576  ', '0.91561031  '], time:0.00694895ms
         out_f32x4: ['0.27619576  ', '0.91561031  '], time:0.00487852ms
        out_f32_th: ['0.27619576  ', '0.91561031  '], time:0.00825715ms
-------------------------------------------------------------------------------------
           out_f16: ['0.27612305  ', '0.91552734  '], time:0.00662899ms
         out_f16x2: ['0.27612305  ', '0.91552734  '], time:0.00528407ms
         out_f16x8: ['0.27612305  ', '0.91552734  '], time:0.00506496ms
     out_f16x8pack: ['0.27612305  ', '0.91552734  '], time:0.00361753ms
        out_f16_th: ['0.27612305  ', '0.91552734  '], time:0.00771737ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=1024, K=4096
           out_f32: ['0.07250839  ', '0.12893374  '], time:0.01215029ms
         out_f32x4: ['0.07250839  ', '0.12893374  '], time:0.00853109ms
        out_f32_th: ['0.07250839  ', '0.12893374  '], time:0.00838566ms
-------------------------------------------------------------------------------------
           out_f16: ['0.07250977  ', '0.12890625  '], time:0.01154637ms
         out_f16x2: ['0.07250977  ', '0.12890625  '], time:0.01020956ms
         out_f16x8: ['0.07250977  ', '0.12890625  '], time:0.01049662ms
     out_f16x8pack: ['0.07250977  ', '0.12890625  '], time:0.00484633ms
        out_f16_th: ['0.07250977  ', '0.12890625  '], time:0.00788140ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=2048, K=1024
           out_f32: ['0.0         ', '0.0         '], time:0.00900364ms
         out_f32x4: ['0.0         ', '0.0         '], time:0.00489092ms
        out_f32_th: ['0.0         ', '0.0         '], time:0.00787544ms
-------------------------------------------------------------------------------------
           out_f16: ['0.0         ', '0.0         '], time:0.00855136ms
         out_f16x2: ['0.0         ', '0.0         '], time:0.00422597ms
         out_f16x8: ['0.0         ', '0.0         '], time:0.00462198ms
     out_f16x8pack: ['0.0         ', '0.0         '], time:0.00363016ms
        out_f16_th: ['0.0         ', '0.0         '], time:0.00775146ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=2048, K=2048
           out_f32: ['0.0         ', '0.0         '], time:0.01215339ms
         out_f32x4: ['0.0         ', '0.0         '], time:0.00813413ms
        out_f32_th: ['0.0         ', '0.0         '], time:0.00860500ms
-------------------------------------------------------------------------------------
           out_f16: ['0.0         ', '0.0         '], time:0.01154780ms
         out_f16x2: ['0.0         ', '0.0         '], time:0.00901484ms
         out_f16x8: ['0.0         ', '0.0         '], time:0.00888395ms
     out_f16x8pack: ['0.0         ', '0.0         '], time:0.00487232ms
        out_f16_th: ['0.0         ', '0.0         '], time:0.00787640ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=2048, K=4096
           out_f32: ['0.0         ', '1.24274826  '], time:0.02253866ms
         out_f32x4: ['0.0         ', '1.24274826  '], time:0.01534677ms
        out_f32_th: ['0.0         ', '1.24274826  '], time:0.04056597ms
-------------------------------------------------------------------------------------
           out_f16: ['0.0         ', '1.24316406  '], time:0.02144694ms
         out_f16x2: ['0.0         ', '1.24316406  '], time:0.01887226ms
         out_f16x8: ['0.0         ', '1.24316406  '], time:0.01928806ms
     out_f16x8pack: ['0.0         ', '1.24316406  '], time:0.00811267ms
        out_f16_th: ['0.0         ', '1.24316406  '], time:0.01040673ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=4096, K=1024
           out_f32: ['0.0         ', '0.39495975  '], time:0.01634669ms
         out_f32x4: ['0.0         ', '0.39495975  '], time:0.00815415ms
        out_f32_th: ['0.0         ', '0.39495975  '], time:0.00910711ms
-------------------------------------------------------------------------------------
           out_f16: ['0.0         ', '0.39501953  '], time:0.01556730ms
         out_f16x2: ['0.0         ', '0.39501953  '], time:0.00694680ms
         out_f16x8: ['0.0         ', '0.39501953  '], time:0.00806046ms
     out_f16x8pack: ['0.0         ', '0.39501953  '], time:0.00490713ms
        out_f16_th: ['0.0         ', '0.39501953  '], time:0.00785518ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=4096, K=2048
           out_f32: ['0.0         ', '0.1470257   '], time:0.02254725ms
         out_f32x4: ['0.0         ', '0.1470257   '], time:0.01469660ms
        out_f32_th: ['0.0         ', '0.1470257   '], time:0.03984213ms
-------------------------------------------------------------------------------------
           out_f16: ['0.0         ', '0.14697266  '], time:0.02126026ms
         out_f16x2: ['0.0         ', '0.14697266  '], time:0.01639915ms
         out_f16x8: ['0.0         ', '0.14697266  '], time:0.01609683ms
     out_f16x8pack: ['0.0         ', '0.14697266  '], time:0.00815415ms
        out_f16_th: ['0.0         ', '0.14697266  '], time:0.01040459ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=4096, K=4096
           out_f32: ['0.50983185  ', '0.0         '], time:0.18850398ms
         out_f32x4: ['0.50983185  ', '0.0         '], time:0.18800068ms
        out_f32_th: ['0.50983185  ', '0.0         '], time:0.20505428ms
-------------------------------------------------------------------------------------
           out_f16: ['0.50976562  ', '0.0         '], time:0.04072070ms
         out_f16x2: ['0.50976562  ', '0.0         '], time:0.03618884ms
         out_f16x8: ['0.50976562  ', '0.0         '], time:0.03668690ms
     out_f16x8pack: ['0.50976562  ', '0.0         '], time:0.01468301ms
        out_f16_th: ['0.50976562  ', '0.0         '], time:0.03995824ms
-------------------------------------------------------------------------------------
```