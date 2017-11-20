---
title: "IDebugFunctionObject2::Evaluate |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58c15872b035660c2e0103a1a9ff69822b250a45
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
関数を呼び出すし、オブジェクトとして結果の値を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppParams`  
 [in]配列[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)入力パラメーターを表すオブジェクト。 これらの各パラメーターは、このインターフェイスの作成方法のいずれかを使用して作成されました。  
  
 `dwParams`  
 [in]パラメーターの数、`ppParams`配列。  
  
 `dwEvalFlags`  
 [in]フラグの組み合わせ、 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)評価を実行する方法を指定する列挙体です。  
  
 `dwTimeout`  
 [in]このメソッドから戻る前に待機するミリ秒単位で最大の時間を指定します。 使用して**無限**無制限に待機します。  
  
 `ppResult`  
 [out]返します、 **IDebugObject**関数オブジェクトとしての値を表すです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)