Welcome to MRITK's documentation!
===================================

Model Runtime Insight ToolKit (MRITK) 主要设计用于深度学习模型编译前，预评估和分析深度学习模型在用户指定的设备上的运行时状态，包括模型文件转换，模型结构简化，模型量化，模型效果评估，计算模型参数等指标，硬件计算性能指标等，支持用户自定义硬件。

Check out the :doc:`usage` section for further information, including
how to :ref:`installation` the project.

.. note::

   This project is under active development.

Contents
--------

## API 
主体API分为：
## model
   
   Model 部分主要为 模型的CURD功能接口；底层有统一模型支持类型的注册机制；上层暴露出统一的亿铸自定义类型； X（tensorflow，pytorch，caffe, etc.） (original x model types) - > Y（yi）(中间转换态 可选) -> Z（zhu）(最终计算时模型) 

- model.core
- model.regstier
- model.tansformat
- model.summarize
- model.simplify
- model.quantize
- model.evaluate

 ## runtime
   
   运行时主要对模型运行时的各种硬件、模型参数等进行适配，通过模拟运行时的状态来生成预计的性能指标报告。设计主要包含 runtime.profile, runtime.benchmark, runtime.device 三个部分。该部分接口不对模型格式做统一要求，既可以匹配市面上的框架优化后的模型，也可以直接用我们上面提供的优化流程下的模型。
   
- runtime.profiler
- rumtime.benchmark
- rumtime.device 
- runtime.summary  

 ## insight
   
   Insight 部分主要包含生成报告，支持各种模型的对应报告。这是insight的部分的功能，另外 insight也会构建不同模型优化流程下的benchmark回收比较；profiler 分析和比较；summary 回收和比较。insight属于对前面两步骤的主要概括，给用户产出相应的报告，这部分能够给用户更直观的报告展示和性能分析，方便用户做出决策。
  
- insight.reporter
- insight.bench
- insight.profiling
- insight.mlperf
- insight.prediction
- insight.evaluation

## Tools 
工具，主要放入一些工具性质的接口，用于执行基本的兼容性、改进性，转换性质的工作。

- tools.datasets  数据集，用于深度学习的模型数据集；
- tools.matrics   各种评估模型的指标类；
- tools.fetch_model 下载各种模型的接口
- tools.save_model 保存自己的模型到指定的地方


.. toctree::

   usage
   api
