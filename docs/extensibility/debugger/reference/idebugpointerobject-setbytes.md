---
title: IDebugPointerObject::SetBytes |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a8234117d7965c4f2e471855d39ed0c3cee1f88c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
一連の連続するバイトを指す値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwStart`  
 [in]指されるオブジェクトの先頭からのバイト単位のオフセット。  
  
 `dwCount`  
 [in]設定するバイト数。  
  
 `pBytes`  
 [in]新しい値を表すバイトの配列。 この値は、指定されたオフセットから始まる、オブジェクトに格納されます。  
  
 `pdwBytes`  
 [out]実際のバイト数の設定を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 場合、このメソッドは使用これによって表されるポインター [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)プリミティブ型またはプリミティブ型 (つまり、単純なバイト シーケンスによって表すことができる配列) の単純な配列を指します。 これは、`IDebugPointerObject`オブジェクトが null 参照 (メモリ内のアドレスを指している必要があります) にすることはできません。  
  
## <a name="see-also"></a>関連項目  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)