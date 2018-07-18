---
title: IDebugFunctionObject2::Evaluate |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8196eb45b2fe7eccbff5c23a7ffc58fd3eb59282
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112702"
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