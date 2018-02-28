---
title: "IDebugPointerObject::SetBytes |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9bab2459d2de40fdc3ea44fe7e5e92c138a5f006
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)