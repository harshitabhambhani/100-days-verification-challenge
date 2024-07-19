# 100 Days Verification Challenge - Day 40 - Parameters

## 1. What are the three kinds of parameters?

In Verilog, there are mainly three types of parameters:
- **`parameter`**: Used for defining constants that are fixed during module instantiation. They can be overridden during module instantiation.
- **`specparam`**: Used for specifying timing parameters for delays in timing checks. These parameters are typically used in `specify` blocks and are not intended for module instantiation.
- **`localparam`**: Similar to `parameter`, but cannot be overridden during module instantiation. They are intended to be used for internal constants within a module.

## 2. How can I override a module's parameter values?

You can override a module's parameter values during instantiation using the following syntax:
```verilog
module my_module #(parameter PARAM_NAME = DEFAULT_VALUE) (...);
  // module definition
endmodule

// Instantiating the module with overridden parameter
my_module #(.PARAM_NAME(NEW_VALUE)) instance_name (...);
```
In this example, `PARAM_NAME` is overridden with `NEW_VALUE` when `my_module` is instantiated.

## 3. What are the rules governing parameter assignments?

- **Default Values**: Parameters have default values specified in the module definition.
- **Overriding**: Parameters can be overridden during module instantiation.
- **Data Types**: Parameters can be integers, real numbers, strings, or user-defined types.
- **Scope**: Parameters defined in a module are local to that module unless they are overridden during instantiation.

## 4. How do I prevent selected parameters of a module from being overridden during instantiation? 

To prevent parameters from being overridden during instantiation, use `localparam` instead of `parameter`. 
Example:
```verilog
module my_module #(localparam PARAM_NAME = DEFAULT_VALUE) (...);
  // module definition
endmodule
```
In this case, `PARAM_NAME` cannot be overridden when the module is instantiated.

## 5. Differences Between `define`, `parameter`, and `defparam`

- **`define`**: A preprocessor directive used to define macros. These are not type-checked and are replaced by the preprocessor before compilation.
  ```verilog
  `define MACRO_NAME VALUE
  ```
- **`parameter`**: Used for defining constants that can be overridden during module instantiation. They are type-checked.
  ```verilog
  parameter PARAM_NAME = VALUE;
  ```
- **`defparam`**: Used to override parameters of instantiated modules after they have been instantiated. This is generally discouraged in favor of direct parameter overrides during instantiation.
  ```verilog
  defparam instance_name.PARAM_NAME = NEW_VALUE;
  ```

## 6. What are the pros and cons of specifying the parameters using the defparam construct vs. specifying during instantiation? 

- **Pros of `defparam`**:
  - Allows modification of parameters after instantiation.
- **Cons of `defparam`**:
  - Less explicit and less readable.
  - Can make code harder to understand and maintain.
  - Generally discouraged in favor of specifying parameters during instantiation.

## 7. What is the difference between the specparam and parameter constructs?

- **`specparam`**: Used within `specify` blocks for timing checks. It defines timing constraints or delays.
  ```verilog
  specify
    specparam t_rise = 200;
    specparam t_fall = 150;
  endspecify
  ```
- **`parameter`**: Used for defining constants that can be used throughout the module and can be overridden during instantiation.

## 8. What are derived parameters? When are derived parameters useful, and what are their limitations?

- **Derived Parameters**: These are parameters computed from other parameters or constants.
  ```verilog
  parameter BASE_WIDTH = 8;
  parameter DERIVED_WIDTH = BASE_WIDTH * 2;
  ```
- **Usefulness**: They help in creating parameters that are based on other parameters, making the design more modular.
- **Limitations**: Derived parameters can make the code harder to understand if not used carefully. They can also lead to unintended results if the base parameters change.

## 9. Explain overriding of parameters using defparam with an example.

Here’s an example:
```verilog
module my_module #(parameter PARAM_NAME = DEFAULT_VALUE) (...);
  // module definition
endmodule

my_module instance_name (...);
defparam instance_name.PARAM_NAME = NEW_VALUE;
```
In this example, `PARAM_NAME` is overridden using `defparam` after the module is instantiated. Note that this method is generally not recommended.

## 10. Explain the meaning of following code snippets:-

- **i. `specify` and `specparam`**:
  ```verilog
  specify
    specparam t_rise = 200;
    specparam t_fall = 150;
  endspecify
  ```
  This snippet defines timing parameters `t_rise` and `t_fall` used in timing checks. The `specify` block is used for specifying timing constraints and checks.

- **ii. `parameter` Declaration**:
  ```verilog
  parameter BUS_WIDTH = 32;
  parameter DATA_WIDTH = 64;
  ```
  This snippet declares two parameters: `BUS_WIDTH` and `DATA_WIDTH`, with default values of 32 and 64, respectively. These parameters can be overridden when the module is instantiated.

