# autogen_iolibs

## What is Autogen IOlibs
This python project defines a language to describe the IO modules of any MCU and automatically generate the IO libraries for C or C++ to manipulate such registers

The language must be simple but it must allow to describe whatever you need for any possible IO module including documentation

## The language
This is de 1st version of the language:

### Structural Object Constructions

#### Memory mapped IO Modules
```C
BMOD module_name [index_letter] // Start an IO module description
```
```C
FMOD module_name // Finishes an IO module description
```
#### Module Registers
```C
BREG register_name [index_letter] // Start a register description
```

```C
FREG register_name // Finishes a register descrition
```
#### Register Bitfields
```C
BBIT bitfield_name MSB LSB [index_letter] // Start a bitfield description
```

```C
FBIT bitfield_name // Finishes a bitfield
```

#### Module Channels
```C
BCH channel_name [index_letter] // Start a channel description
```

```C
FCH channel_name // Finish a channel
```

#### Module Slices
```C
BSLICE slice_name [index_letter] // Start an slice description
```

```C
FSLICE slice_name // Finishes an slice
```
### Instanciation Construction

#### Single Instanciation
```C
INST module_name/register_name/channel_name/slice_name [index] // Instancia un modulo, un registro, un canal o un slice, así es posible describir los objetos una vez y usarlos multiples veces en la descripción de otros objetos de mayor jerarquía. En caso de los modulos permite instanciar multiples variantes de un mismo modulo
```

#### Multiple Instanciation
```C
BRPT num [index_type index_letter] // Instanciate an structural objects multiple times reducing the amount of code required to describe a module. The parameter num indicates the number of instances to generate and index_type defines the type of indexing to perform: numeric or alphabetic.
```

```C
FRPT // Finishes a multiple instanciation
```

### Properties

#### Module Address
#### Module Type
#### Module Address Aliases
#### Register Offset
#### Access Type
#### Reset Value
#### Description
#### Comentary
#### Value

### Target and autogen options
