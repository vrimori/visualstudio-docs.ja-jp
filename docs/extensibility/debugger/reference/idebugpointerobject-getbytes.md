---
title: IDebugPointerObject::GetBytes |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 106472037873045b0b30381e6ce901c89b342bae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916550"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
一連の連続するバイトとして指す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwStart`  
 [in]指すオブジェクトの先頭からのバイト単位のオフセット。  
  
 `dwCount`  
 [in]取得するバイト数。  
  
 `pBytes`  
 [入力、出力]一連の連続するバイトの値が入力する配列が指すオブジェクトから指定されたオフセットから開始します。  
  
 `pdwBytes`  
 [out]実際に取得するバイト数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 場合、このメソッドが使用されるこれによって表されるポインター [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)プリミティブ型またはプリミティブ型 (つまり、単純なバイト シーケンスで表すことができる配列) の単純な配列を指します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)