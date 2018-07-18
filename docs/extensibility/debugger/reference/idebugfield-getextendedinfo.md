---
title: IDebugField::GetExtendedInfo |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 63bf182e4e8b17133fbefd4f4a19c4b8b4a458e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110316"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
このメソッドは、フィールドに関する情報を拡張を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `guidExtendedInfo`  
 [in]返される情報を選択します。 次の値を指定できます。  
  
|[値]|説明|  
|-----------|-----------------|  
|`guidConstantValue`|バイト シーケンスとしての値。|  
|`guidConstantType`|型のシグネチャと型。|  
  
 `prgBuffer`  
 [out]拡張された情報を返します。  
  
 `pdwLen`  
 [入力、出力].拡張された情報のサイズをバイト単位で返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 現時点では、このメソッドは、型または定数の値だけを返します。 呼び出し元で返されるバッファーを解放する必要があります`prgBuffer`呼び出して COM の`CoTaskMemFree`関数 (C++) または<xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>(C# の場合)。  
  
## <a name="see-also"></a>関連項目  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)