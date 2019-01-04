---
title: IDebugDocumentContext2::Compare |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a4475dd8031dd75a35dda8950b8005886ec9b47
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866700"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
このドキュメントのコンテキスト ドキュメント コンテキストの指定した配列を比較します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `compare`  
 [in]値、 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)比較の種類を指定する列挙体。  
  
 `rgpDocContextSet`  
 [in]配列の[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)比較対象のドキュメント コンテキストを表すオブジェクト。  
  
 `dwDocContextSetLen`  
 [in]比較するドキュメントのコンテキストの配列の長さ。  
  
 `pdwDocContext`  
 [out]インデックスを返します、`rgpDocContextSet`比較で一致する最初のドキュメント コンテキストの配列。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`一致が見つかった場合します。 返します`S_FALSE`一致が検出されない場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)を実装する同じデバッグ エンジンによって、配列に渡されたオブジェクトを実装する必要が、`IDebugDocumentContext2`オブジェクト。 それ以外に呼び出される比較は無効です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)