#se
* *The TensorRT runtime can be used by multiple threads simultaneously, so long as each object uses a different execution ==context==.* ^8ebe58
* To run TRT thread safe we need to use following construction:
```python
with engine.create_execution_context() as context:
    ctx = cuda.Context.attach()
    inputs, outputs, bindings, stream = allocate_buffer()
    ctx.detach()
```
**[link](https://stackoverflow.com/questions/49595175/pycuda-context-error-when-using-flask)**
