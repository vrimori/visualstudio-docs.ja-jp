---
title: IDebugPointerObject::GetBytes |Microsoft ドキュメント
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
ms.openlocfilehash: 1459a0f99dd4b0ea9c9e998404b1ffe1733cb3bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115867"
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
 [in]指されるオブジェクトの先頭からのバイト単位のオフセット。  
  
 `dwCount`  
 [in]取得するバイト数。  
  
 `pBytes`  
 [入力、出力].値を使用して一連の連続するバイトとして格納される、配列が指すオブジェクトから、指定したオフセットで開始します。  
  
 `pdwBytes`  
 [out]実際に取得されるバイト数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 場合、このメソッドは使用これによって表されるポインター [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)プリミティブ型またはプリミティブ型 (つまり、単純なバイト シーケンスによって表すことができる配列) の単純な配列を指します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)