---
Description: Multiplies every value in the buffer by a constant value.
ms.assetid: 3d7ef530-b83a-4123-a2ed-fff2b21378ee
title: ID3DXPRTBuffer::ScaleBuffer method
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# ID3DXPRTBuffer::ScaleBuffer method

Multiplies every value in the buffer by a constant value.

## Syntax


```C++
HRESULT ScaleBuffer(
  [in] FLOAT Scale
);
```



## Parameters

<dl> <dt>

*Scale* \[in\]
</dt> <dd>

Type: **[**FLOAT**](https://msdn.microsoft.com/4553cafc-450e-4493-a4d4-cb6e2f274d46)**

Constant value used to scale the buffer. Every value in the buffer is replaced by the product of this value and the original buffer value.

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/windows/desktop/455d07e9-52c3-4efb-a9dc-2955cbfd38cc)**

If the method succeeds, the return value is S\_OK. If the method fails, the following value will be returned.

## Requirements



|                    |                                                                                        |
|--------------------|----------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX9Mesh.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3dx9.lib</dt> </dl>   |



## See also

<dl> <dt>

[ID3DXPRTBuffer](id3dxprtbuffer.md)
</dt> </dl>

 

 



