---
title: IDebugPointerObject::SetBytes |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 347f7d2dc88a5e4e76134a7e60832542c9362b0a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938449"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

一連の連続するバイトを指す値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]指すオブジェクトの先頭からのバイト単位のオフセット。  
  
 `dwCount`  
 [in]設定するバイト数。  
  
 `pBytes`  
 [in]新しい値を表すバイトの配列。 この値は、指定されたオフセットから始まる、オブジェクトに格納されます。  
  
 `pdwBytes`  
 [out]実際のバイト数の設定を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 場合、このメソッドが使用されるこれによって表されるポインター [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)プリミティブ型またはプリミティブ型 (つまり、単純なバイト シーケンスで表すことができる配列) の単純な配列を指します。 これは、`IDebugPointerObject`オブジェクトが null 参照 (メモリ内のアドレスを指している必要があります) にすることはできません。  
  
## <a name="see-also"></a>関連項目  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)

