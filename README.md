# autogen_iolibs
This python project defines a language to describe the IO modules of any MCU and automatically generate the IO libraries for C or C++ to manipulate such registers

The language must be simple but it must allow to describe whatever you need for any possible IO module including documentation

This is de 1st version of the language:

BMOD module_name // Start an IO module description
FMOD module_name // Finish an IO module description

BREG register_name // Start a register description
EREG register_name // Finish a register descrition
