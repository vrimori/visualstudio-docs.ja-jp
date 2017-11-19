---
title: "IDebugField::GetExtendedInfo |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetExtendedInfo
helpviewer_keywords: IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5b52c5634b4b34edf11ddb8a56317cc237063bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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
  
|値|説明|  
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