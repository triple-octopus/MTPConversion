# MTPConversion

This is a tutorial on how to convert a non MTP model into an MTP model.

# Get the Models

First you need your base model, for this I am using https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive

I use a quantized model for sure (Q4_K_P) but it is not relevant at all as the converter does not care.

Then you need an MTP version of your model, I found mine at https://huggingface.co/am17an/Qwen3.6-35BA3B-MTP-GGUF

# The Converter
Downloda the converter.py either from this repo, or from the original creator https://huggingface.co/havenoammo/Qwen3.6-27B-MTP-UD-GGUF/blob/main/convert.py

# llama.cpp Version

Before converting anything, make sure you have llama.cpp with version AT LEAST b9180, I used the latest at this time (b9190).

# The Conversion

I placed the convert.py in the root folder of llama.cpp, just because I like to keep things organized.

My base model is named Qwen3.635BA3BA-Q4_K_P.gguf and the MTP model is named Qwen3.6-35BA3B-MTP.gguf, both are placed in a subfolder called Models.

I opened the python file and checked the import section and made sure that I had all packages installed (used `pip install gguf` because I didn't have it)

Then I ran the command as such `python convert.py .\Models\Qwen3.635BA3BA-Q4_K_P.gguf .\Models\Qwen3.6-35BA3B-MTP.gguf Qwen3.6-35BA3B-MTP-UNCENSORED-Q4_K_P.gguf`

The first argument is your base model, the second argument is the MTP version of your model, and the last argument is the output model name.

# Arguments

When I ran llama.cpp I made sure to add the MTP arguments `--spec-type draft-mtp --spec-draft-n-max 2` to my original llama.cpp command.

# Benchmarks

On a 12GB 3080Ti, 32GB DDR5 system, the non MTP model ran at anywhere from 42 to 32 tokens per second, the MTP model runs now from 66 up to 72 tokens/s.

This can be applied to any model (I think) as long as you have an MTP version of your model.
