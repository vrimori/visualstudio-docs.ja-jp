---
title: "IDebugDocumentContext2::Compare |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentContext2::Compare
helpviewer_keywords: IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 550695aa52f1c913b25fc56975eb5c6e36b4c091
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
ドキュメントのコンテキストの指定した配列にこのドキュメントのコンテキストを比較します。  
  
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
 [in]値、 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)比較の種類を指定する列挙です。  
  
 `rgpDocContextSet`  
 [in]配列[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)と比較されているドキュメントのコンテキストを表すオブジェクト。  
  
 `dwDocContextSetLen`  
 [in]比較するドキュメントのコンテキストの配列の長さ。  
  
 `pdwDocContext`  
 [out]インデックスを返します、`rgpDocContextSet`比較で一致する最初のドキュメント コンテキストの配列。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`場合は、一致が見つかりませんでした。 返します`S_FALSE`一致が検出されない場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)を実装する、同じデバッグ エンジンで配列に渡されたオブジェクトを実装する必要があります、`IDebugDocumentContext2`オブジェクトの場合は、呼び出されて、比較は無効です。  
  
## <a name="see-also"></a>参照  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)