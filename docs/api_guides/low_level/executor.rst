..  _api_guide_executor:

##########
执行引擎
##########

:code:`Executor` 实现了一个简易的执行器，所有的操作在其中顺序执行。你可以在 Python 脚本中运行 :code:`Executor` 。

 :code:`Executor` 的逻辑非常简单。建议在调试阶段用 :code:`Executor` 在一台计算机上完整地运行模型，然后转向多设备或多台计算机计算。

 :code:`Executor` 在构造时接受一个 :code:`Place` ，它既可能是 :ref:`api_fluid_CPUPlace` 也可能是 :ref:`api_fluid_CUDAPlace` 。

.. code-block:: python
    # 首先创建 Executor。
    place = fluid.CUDAPlace(0) if use_cuda else fluid.CPUPlace()
    exe = fluid.Executor(place)
    # 运行启动程序仅一次。
    exe.run(fluid.default_startup_program())

    # 直接运行主程序。
    loss, = exe.run(fluid.default_main_program(),
                    feed=feed_dict,
                    fetch_list=[loss.name])
简单样例请参照 `basics_fit_a_line <../../beginners_guide/basics/fit_a_line/README.cn.html>`_

- 相关 API :
 - :ref:`cn_api_fluid_Executor`
