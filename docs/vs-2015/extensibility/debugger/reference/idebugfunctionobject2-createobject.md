---
title: IDebugFunctionObject2::CreateObject |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b9a744588913e5f39b8b493552327f944ae923a4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304955"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

評価のフラグ設定、およびタイムアウト値を指定されたコンス トラクターを使用するオブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pConstructor`  
 [in][IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)を作成するオブジェクトのコンス トラクターを表すオブジェクト。  
  
 `dwArgs`  
 [in]パラメーターの数、`pArg`配列。 コンス トラクターに渡されるパラメーターの数を表します。  
  
 `pArgs`  
 [in]配列の[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)コンス トラクターに渡されるパラメーターを表すオブジェクト。  
  
 `dwEvalFlags`  
 [in]フラグの組み合わせ、 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)評価を実行する方法を指定する列挙体。  
  
 `dwTimeout`  
 [in]このメソッドから戻る前に待機するミリ秒単位で最大時間。 使用**無限**を無期限に待機します。  
  
 `ppObject`  
 [out]返します、 **IDebugObject**新しく作成されたオブジェクトを表します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 クラス、またはパラメーターであるコンス トラクターを必要とするその他の複合型のインスタンスを表すオブジェクトを作成するには、このメソッドを呼び出します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)

