# Weekly Report

- [Weekly Report](#weekly-report)
  - [2024-06-20](#2024-06-20)

## 2024-06-20
1. Successfully installed [Sionna-RT on Windows PC](./Installation%20Guide.md##2-sionna-installation-via-pip):
   1. Managed to install version 0.15.0, which is compatible with the current Windows version.
   2. Noted that the latest version available from Nvidia for Ubuntu is 0.18.0.
2. Conducted a test on the [Hello_world.ipynb](../Hello_World.ipynb) template, sourced from the [NVIDIA template](https://nvlabs.github.io/sionna/examples/Hello_World.html).
  - The Hello World test failed at the second step due to incompatibility issues with version 0.15.0.
    <details>
    <summary>Error Log</summary>
    
    ```python
    ---------------------------------------------------------------------------
    TypeError                                 Traceback (most recent call last)
    Cell In[7], line 4
          2 num_bits_per_symbol = 4 # 16-QAM has four bits per symbol
          3 binary_source = sionna.utils.BinarySource()
    ----> 4 b = binary_source(batch_size=batch_size, num_bits_per_symbol=num_bits_per_symbol)
          5 b

    File D:\Users\bmw-ece-ntust\Documents\GitHub\wifi-sionna\venv\Lib\site-packages\keras\src\utils\traceback_utils.py:122, in filter_traceback.<locals>.error_handler(*args, **kwargs)
        119     filtered_tb = _process_traceback_frames(e.__traceback__)
        120     # To get the full stack trace, call:
        121     # `keras.config.disable_traceback_filtering()`
    --> 122     raise e.with_traceback(filtered_tb) from None
        123 finally:
        124     del filtered_tb

    File ~\AppData\Local\Programs\Python\Python312\Lib\inspect.py:3267, in Signature.bind(self, *args, **kwargs)
      3262 def bind(self, /, *args, **kwargs):
      3263     """Get a BoundArguments object, that maps the passed `args`
      3264     and `kwargs` to the function's signature.  Raises `TypeError`
      3265     if the passed arguments can not be bound.
      3266     """
    -> 3267     return self._bind(args, kwargs)

    File ~\AppData\Local\Programs\Python\Python312\Lib\inspect.py:3180, in Signature._bind(self, args, kwargs, partial)
    ...
      3181 else:
      3182     # We have a positional argument to process
      3183     try:

    TypeError: missing a required argument: 'inputs'
    ```
  - **Proposed Solution**: Install Sionna on an Ubuntu machine and retest using version 0.18.0.