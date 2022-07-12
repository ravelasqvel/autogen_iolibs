# autogen_iolibs

## What is Autogen IOlibs?
This python project defines a language to describe the IO modules of any MCU and automatically to generate the IO libraries for C or C++ to manipulate module's registers and register bitfields

The language must be simple but it must allow to describe whatever you need for any possible IO module including documentation

## The language
This is de 1st version of the language:

### Structural Objects Constructions
There are three main structural components in a memory mapped module (M3), the module itself, the registers that make the module up, and the bitfields defined into the register. Describing a M3 implies desclarating the module and all the register used by that module. Because a module might have some repeated register the process of declaration and instantiation is splited. A register can be declarated in a generic way with its name containing some index which value (numeric or alphabetic) can be espicified later on the instantiation. Register might be accessed as whole or through bitfields defined in the register. A register declaration define all the bitfields in a register in case they exist.

#### Memory mapped modules
To start the description of a M3 use de following format. The parameter module_name is a short string that will be used by the automatic code generation tool to  reference the specific module. Optional, an alphanumeric subfix can be attached to the module using the parameter index_letter, this is usful for example when an MCU have multiple identical modules, for example, UART0 ,UART1, UART2, etc. This avoids to describe each module indepently. Index_letter only indicate a letter that will be used at the instantiation for attaching the final subfix.
```C
BMOD module_name [index_letter] // Start an IO module description
```
To finish an M3 description use the following sequen
```C
FMOD module_name // Finishes an IO module description
```
#### Module Registers
To start the description of a register use de following format. The parameter register_name is a short string that will be used by the automatic code generation tool to  reference the specific register. Do not include the Module name with the register name, this will be done by the code generator. Optional, an alphanumeric subfix can be attached to the register using the parameter index_letter, this is usful for example when an module have multiple identical registers, for example, UART0 ,UART1, UART2, etc. This avoids to describe each module indepently. Index_letter only indicate a letter that will be used at the instantiation for attaching the final subfix.
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
