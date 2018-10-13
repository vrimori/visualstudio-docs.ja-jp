---
title: IDebugDocumentContext2::Compare |Microsoft Docs
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
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81ff040788ba1ed353a9d2c413b4fc89aaf0b390
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250576"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このドキュメントのコンテキスト ドキュメント コンテキストの指定した配列を比較します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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

