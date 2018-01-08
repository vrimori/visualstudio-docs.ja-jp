---
title: "IEnumDebugCustomAttributes::Next |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCustomAttributes::Next
helpviewer_keywords: IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e32049d2c3b6b210ed1627f133ceb0ace4063abd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugcustomattributesnext"></a>IEnumDebugCustomAttributes::Next
列挙のシーケンス内のカスタム属性の指定した数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next (   
   ULONG      celt,  
   CODE_PATH* rgelt,  
   ULONG*     pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                        celt,   
   out IDebugCustomAttribute[] rgelt,   
   ref uint                    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]取得する要素の数。 また、最大のサイズを指定、`rgelt`配列。  
  
 `rgelt`  
 [out]配列[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)格納するオブジェクト。  
  
 `pceltFetched`  
 [out]実際に返される要素の数を返します`rgelt`です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`要求された要素数より少ないは返されませんでした。 それ以外の場合、エラー コードを返します。  
  
## <a name="see-also"></a>参照  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)