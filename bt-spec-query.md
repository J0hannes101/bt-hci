# 7.7.65.38. LE Read All Remote Features Complete event (7.7.65.38)
**Link:** https://www.bluetooth.com/wp-content/uploads/Files/Specification/HTML/Core_v6.3/out/en/host-controller-interface/host-controller-interface-functional-specification.html#UUID-990b9148-5d60-5e33-4f84-4f5cbc968549

**Volume:** HCI

###### 7.7.65.38. LE Read All Remote Features Complete event

```
────────────────────────────────────┬─────────┬─────────────────────────────────────────────────────────────────────────
Event                               │Event    │Event Parameters                                                         
                                    │Code     │                                                                         
────────────────────────────────────┼─────────┼─────────────────────────────────────────────────────────────────────────
HCI_LE_Read_All_Remote_­Features_­Comp│0x3E     │Subevent_Code,                                                           
lete                                │         │                                                                         
                                    │         │Status,                                                                  
                                    │         │                                                                         
                                    │         │Connection_Handle,                                                       
                                    │         │                                                                         
                                    │         │Max_Remote_Page,                                                         
                                    │         │                                                                         
                                    │         │Max_Valid_Page,                                                          
                                    │         │                                                                         
                                    │         │LE_Features                                                              
────────────────────────────────────┴─────────┴─────────────────────────────────────────────────────────────────────────
```

**Description:**

This event is used to indicate the completion of the process of the Controller obtaining the features supported by the
remote Bluetooth device specified by the Connection_Handle event parameter.

The Max_Remote_Page parameter specifies the highest-numbered page of the remote device’s supported LE features that
contains at least one bit set to 1; all higher-number pages therefore only contain zeroes. The Max_Valid_­Page parameter
specifies the highest-numbered page of features that the Controller has obtained from the remote device or, if it has
obtained all pages from 1 to Max_Remote_­Page, then any value greater than or equal to Max_Remote_­Page.

The LE_Features parameter contains the LE features. The Controller shall set all pages between 0 and Max_Valid_­Page to
valid data and shall set all higher-numbered pages to all zero bits.

### Note

Note: If Max_Valid_Page ≥ Max_Remote_Page, then all pages will contain valid data, which will be all zero bits for pages
numbered greater than Max_Remote_­Page.

If the feature mask is requested more than once while a connection exists between the two devices, then the second and
subsequent requests may report a cached copy of the feature mask rather than fetching the feature mask again.

**Event parameters:**

```
────────────────┬───────────────
*Subevent_Code:*│*Size: 1 octet*
────────────────┴───────────────
```

```
─────┬─────────────────────────────────────────────────────────────────────
Value│Parameter Description                                                
─────┼─────────────────────────────────────────────────────────────────────
0x2B │Subevent code for the HCI_LE_Read_All_Remote_Features_Complete event.
─────┴─────────────────────────────────────────────────────────────────────
```

```
─────────┬───────────────
*Status:*│*Size: 1 octet*
─────────┴───────────────
```

```
────────┬───────────────────────────────────────────────────────────────────────────────────────────────────────────────
Value   │Parameter Description                                                                                          
────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────
0x00    │HCI_LE_Read_All_Remote_Features command successfully completed.                                                
────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────
0x01 to │HCI_LE_Read_All_Remote_Features command failed to complete. See [[Vol 1] Part F, Controller Error Codes] for a 
0xFF    │list of error codes and descriptions.                                                                          
────────┴───────────────────────────────────────────────────────────────────────────────────────────────────────────────
```

```
────────────────────┬─────────────────────────────────────
*Connection_Handle:*│*Size: 2 octets (12 bits meaningful)*
────────────────────┴─────────────────────────────────────
```

```
──────┬───────────────────────────────────────
Value │Parameter Description                  
──────┼───────────────────────────────────────
0xXXXX│Connection_Handle                      
      │                                       
      │Range 0x0000 to 0x0EFF                 
──────┴───────────────────────────────────────
```

```
──────────────────┬───────────────
*Max_Remote_Page:*│*Size: 1 octet*
──────────────────┴───────────────
```

```
────┬───────────────────────────────────────────────────────────────────────────────────────────────────────────────────
Valu│Parameter Description                                                                                              
e   │                                                                                                                   
────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────
0xXX│The number of the highest-numbered page of the remote device’s supported LE features that contains at least one bit
    │set to 1.                                                                                                          
    │                                                                                                                   
    │Range: 0x00 to 0x0A                                                                                                
────┴───────────────────────────────────────────────────────────────────────────────────────────────────────────────────
```

```
─────────────────┬───────────────
*Max_Valid_Page:*│*Size: 1 octet*
─────────────────┴───────────────
```

```
─────┬───────────────────────────────────────────────────────────────────────────────────────────────────
Value│Parameter Description                                                                              
─────┼───────────────────────────────────────────────────────────────────────────────────────────────────
0xXX │The number of the highest-numbered page of LE_Features that contains valid data.                   
     │                                                                                                   
     │Range: 0x00 to 0x0A                                                                                
─────┴───────────────────────────────────────────────────────────────────────────────────────────────────
```

```
──────────────┬──────────────────
*LE_Features:*│*Size: 248 octets*
──────────────┴──────────────────
```

```
─────────┬─────────────────────────────────────────────────────────────────────────────────────
Value    │Parameter Description                                                                
─────────┼─────────────────────────────────────────────────────────────────────────────────────
0xXX...XX│Bit Mask List of the LE features. See [[Vol 6] Part B, Section 4.6].Feature support  
─────────┴─────────────────────────────────────────────────────────────────────────────────────
```