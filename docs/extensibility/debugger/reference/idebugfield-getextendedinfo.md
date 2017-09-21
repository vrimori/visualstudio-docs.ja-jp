---
title: "IDebugField::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugField::GetExtendedInfo メソッド"
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはフィールドに関する情報を拡張します。  
  
## 構文  
  
```cpp#  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```c#  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### パラメーター  
 `guidExtendedInfo`  
 \[出力\] 返される情報をクリックします。  次の値を指定できます。  
  
|値|Description|  
|-------|-----------------|  
|`guidConstantValue`|バイトのシーケンスとしての値。|  
|`guidConstantType`|型シグネチャとして型。|  
  
 `prgBuffer`  
 \[入力\] 拡張情報を返します。  
  
 `pdwLen`  
 \[入力出力\] のバイト拡張情報のサイズを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 現在このメソッドは型のみまたは定数の値。  呼び出し元はCOM `CoTaskMemFree` の関数 \(C\+\+\) または \(C\#\) <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> を呼び出して `prgBuffer` に返されるバッファーを解放する必要があります。  
  
## 参照  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)