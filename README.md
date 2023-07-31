# **Port Driver based on AUTOSAR Layered Architecture v4.0.3 for Tiva-C (TM4C123GH6PM)**
This is a header file Port.h for the TM4C123GH6PM microcontroller - Port Driver. This Port Driver is based on the AUTOSAR layered architecture v4.0.3 and provides APIs for initializing the Port Driver, setting the direction of a pin, refreshing the port direction, setting pin mode, and getting the version information.

# **Installation**
This header file Port.h should be included in your project's source code directory to use the prt driver for the Tiva-C (TM4C123GH6PM).

# **Usage**
1. Include Port.h header file in your source code.
2. Initialize the Port Driver using Port_Init() function with a pointer to a configuration structure of type Port_ConfigType.
3. Set the direction of a pin using Port_SetPinDirection() function with the pin number and the desired direction.
4. Refresh the direction of the port using Port_RefreshPortDirection() function.
5. Set the mode of a pin using Port_SetPinMode() function with the pin number and the desired mode.
6. Get the version information of the Port Driver using Port_GetVersionInfo() function.

# **Configuration**
This Port Driver doesn't have a configuration tool, so the symbolic names of each Port-Pin in the microcontroller must be defined in the source code by the user. The user also needs to configure the Port_ConfigType structure to initialize the Port Driver with the desired pins' direction, internal resistor, initial value, mode, direction changeability, and mode changeability.

# **Functions**
### **Port_Init**
```
void Port_Init(const Port_ConfigType* ConfigPtr)
```
 Initializes the port driver with the given configuration settings.
### **Port_SetPinDirection**
```
void Port_SetPinDirection(Port_PinType Pin, Port_PinDirectionType Direction)
```
 Sets the direction (input or output) of the given pin.
### **Port_GetVersionInfo**
```
void Port_GetVersionInfo(Std_VersionInfoType* versioninfo)
```
This function retrieves the version information of the PORT driver.
### **Port_SetPinMode**
```
void Port_SetPinMode(Port_PinType Pin, Port_PinModeType Mode)
```
 Sets the mode of the given pin.
 
### **Port_SetPinPullUp**
```
void Port_SetPinPullUp(Port_PinType Pin, boolean activate)
```
This function activates or deactivates the internal pull-up resistor of the specified pin based on the provided parameter.

### **Port_SetPinValue**
```
void Port_SetPinValue(Port_PinType Pin, Port_PinValueType Value)
```
This function sets the logic level of the specified pin based on the provided value parameter. The value parameter should be one of the following values: PORT_PIN_LOW or PORT_PIN_HIGH.

### **Port_GetPinValue**
```
Port_PinValueType Port_GetPinValue(Port_PinType Pin)
```
This function retrieves the logic level of the specified pin and returns the result as a Port_PinValueType variable.
### **Port_GetVersionInfo**
```
void Port_GetVersionInfo(Std_VersionInfoType* versioninfo)
```
 Gets the version information of the port driver.
 
# **External Variables**
extern const Port_ConfigType Port_Configuration: External variable for the port pin configuration set. This variable should be defined in the user's configuration tool.
# **Macros**

- PORT_VENDOR_ID: Vendor ID of the module
- PORT_MODULE_ID: Module ID of the module
- PORT_INSTANCE_ID: Instance ID of the module
- PORT_SW_MAJOR_VERSION: Software major version of the module
- PORT_SW_MINOR_VERSION: Software minor version of the module
- PORT_SW_PATCH_VERSION: Software patch version of the module
- PORT_AR_RELEASE_MAJOR_VERSION: AUTOSAR major version of the module
- PORT_AR_RELEASE_MINOR_VERSION: AUTOSAR minor version of the module
- PORT_PIN_STATUS_INITIALIZED: Status of a pin that has been initialized
- PORT_PIN_STATUS_UNINITIALIZED: Status of a pin that has not been initialized
- PORT_NUM_OF_PORT_PINS: Number of pins in a single port
- PORT_PIN_MODE_DIO: Pin mode for digital input/output
- PORT_PIN_MODE_ADC: Pin mode for analog to digital conversion
- PORT_PIN_MODE_CAN: Pin mode for CAN communication
- PORT_PIN_MODE_DIO_GPT: Pin mode for digital input/output with GPT timer
- PORT_PIN_MODE_DIO_WDG: Pin mode for digital input/output with WDG timer
- PORT_PIN_MODE_FLEXRAY: Pin mode for FlexRay communication
- PORT_PIN_MODE_ICU: Pin mode for input capture unit
- PORT_PIN_MODE_LIN: Pin mode for LIN communication
- PORT_PIN_MODE_MEM: Pin mode for memory access
- PORT_PIN_MODE_PWM: Pin mode for pulse width modulation
- PORT_PIN_MODE_SPI: Pin mode for SPI communication
- PORT_PIN_MODE_UART: Pin mode for UART communication
- PORT_PIN_MODE_I2C: Pin mode for I2C communication
- 
# **API Service Id Macros**
- PORT_INIT_SID: service ID for PORT initialization.
- PORT_SET_PIN_DIRECTION_SID: service ID for setting pin direction.
- PORT_REFRESH_PORT_DIRECTION_SID: service ID for refreshing port direction.
- PORT_GET_VERSION_INFO_SID: service ID for getting version info.
- PORT_SET_PIN_MODE_SID: service ID for setting pin mode.

# **DET Error Codes**
- PORT_E_PARAM_PIN: DET code for invalid Port Pin ID requested.
- PORT_E_DIRECTION_UNCHANGEABLE: DET code for Port Pin not configured as changeable.
- PORT_E_PARAM_CONFIG: DET code for API Port_Init service called with wrong parameter.
- PORT_E_PARAM_INVALID_MODE: DET code for API Port_SetPinMode service called with wrong parameter Mode.
- PORT_E_MODE_UNCHANGEABLE: DET code for API Port_SetPinMode service called when mode is unchangeable.
- PORT_E_UNINIT: DET code for API service called without module initialization.
- PORT_E_PARAM_POINTER: DET Code for APIs called with a Null Pointer.

# **Data Types**
### **Port_ConfigType**
This structure contains the configuration data for the PORT driver. It consists of arrays of pin configurations for each port.

### **Port_PinType**
This typedef represents a binary number that contains the index and port information of a pin. The least significant 4 bits correspond to the index of the pin, while the most significant 4 bits correspond to the index of the port.

### **Port_PinDirectionType**
This enumeration defines the possible directions that can be used with the PORT driver. It consists of two values: PORT_PIN_IN and PORT_PIN_OUT.

### **Port_PinModeType**
This enumeration defines the possible modes that can be used with the PORT driver. It consists of two values: **PORT_PIN_MODE_DIO and PORT_PIN_MODE_PWM.**

### **Port_PinValueType**
This enumeration defines the possible logic levels that can be used with the PORT driver. It consists of two values: PORT_PIN_LOW and PORT_PIN_HIGH.

### **Std_VersionInfoType**
This structure contains the version information of a software component. It consists of the vendor ID, module ID, instance ID, and software version.

## **Symbolic Names for Port Pins**
Symbolic names for each port pin in the microcontroller should be provided by the user in their configuration tool. These names are used to identify each pin in the Port_ConfigType structure.

## **Standard AUTOSAR Types**
The header file includes the standard AUTOSAR types Std_ReturnType and Std_VersionInfoType.

## **Pre-Compile Configuration Header File**
The Port.h header file includes the pre-compile configuration header file Port_Cfg.h, which contains the configuration settings for the port driver.

## **API Service ID Macros**
The header file defines macros for the API service IDs for each function.

## **DET Error Codes**
The header file defines error codes for the DET (Development Error Tracer).


# **AUTOSAR Det Driver**

### **Det_ReportError**
```
void Det_ReportError(uint16_t ModuleId, uint8_t InstanceId, uint8_t ApiId, uint8_t ErrorId)
```
This API is used to report an error to the Development Error Tracer (DET) driver. It takes four parameters: ModuleId, InstanceId, ApiId, and ErrorId. These parameters are used to identify the module, instance, API, and error that caused the error.

## **Implementation Details**
The DIO driver implementation in this repository uses the Development Error Tracer (DET) driver to detect and report errors during runtime. The AUTOSAR-defined error parameter APIs are used to report errors to the DET driver.

When an error is detected in the DIO driver, it calls one of the error parameter APIs to report the error to the DET driver. The DET driver then handles the error according to the configured error policies, which may include logging the error, notifying the system integrator, or triggering a system reset.

For more information about the DET driver and the error parameter APIs used in the DIO driver implementation, you can refer to the AUTOSAR SWS (Software Specification) for the DIO driver. This document provides a detailed description of the driver architecture, functions, and error handling mechanisms.

# **Version Information**
- Module Version: 1.0.0
- AUTOSAR Version: 4.0.3
- Software Version:
    - Major Version: 1
    - Minor Version: 0
    - Patch Version: 0

# **Credits**
This Port Driver was created by Belal Mohamed.
