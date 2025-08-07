# Private Generative AI

To run large language models such as Llama2 or Llama3 on your virtual machine you will need to obtain the models and install some additional requirements with pip.

## Obtain models - For Huggingface we recommend:

1. Clone the models into the AIModelService sub models folder using: `git clone`
   * For large models, like Llama3 70B, this may take some time.

### Running larger models in 4-bit mode to save GPU memory

1. pip install bitsandbytes
2. pip install setuptools
3. pip install accelerate

### Run GGUF format models with our HuggingfaceGenerativeLlamaCpp provider

You will need to install llama-cpp-python from source.

1. Install the CUDA toolkit for your GPU driver.
2. Run the following to build and install llama-cpp-python into the Model Service venv.
   * `set CMAKE_ARGS=-DLLAMA_CUBLAS=ON`
   * `set FORCE_CMAKE=1`
   * `pip install --upgrade --force-reinstall llama_cpp_python --no-cache-dir`
3. When you enable the model, you should see your GPU memory utilisation increase.&#x20;
   * If it does not, the model is loading into conventional memory. Revisit the previous steps to fix this.

***

## Troubleshooting

You may see an error if you have a newer version of the CUDA toolkit installed. You will see an error at the `pip install --upgrade --force-reinstall llama_cpp_python --no-cache-dir` step.

The following steps will stop this issue.

1. Execute: `set CMAKE_ARGS="-DGGML_CUDA=on"`
2. Rerun: `pip install --upgrade --force-reinstall llama_cpp_python --no-cache-dir`
   * This may take up to an hour to build from source.
