# autogen_iolibs
This python project defines a language to describe the IO modules of any MCU and automatically generate the IO libraries for C or C++ to manipulate such registers

The language must be simple but it must allow to describe whatever you need for any possible IO module including documentation

This is de 1st version of the language:

BMOD module_name [index_letter] // Start an IO module description

FMOD module_name // Finish an IO module description

BREG register_name [index_letter] // Start a register description

FREG register_name // Finish a register descrition

BBIT bitfield_name MSB LSB [index_letter] // Start a bitfield description

FBIT bitfield_name // Finish a bitfield

BCH channel_name [index_letter] // Start a channel description

FCH channel_name // Finish a channel

BSLICE slice_name [index_letter] // Start an slice description

FSLICE slice_name // Finish an slice

INST module_name/register_name/channel_name/slice_name [index] // Instancia un modulo, un registro, un canal o un slice, así es posible describir los objetos una vez y usarlos multiples veces en la descripción de otros objetos de mayor jerarquía. En caso de los modulos permite instanciar multiples variantes de un mismo modulo

BRPT num index_type //

FRPT 
