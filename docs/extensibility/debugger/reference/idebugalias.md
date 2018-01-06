---
title: "IDebugAlias |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias
helpviewer_keywords: IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f984f9454aa646663d2888c4241c2ed385188cd7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 変数の数値のエイリアスを表します。 エイリアスは、変数の別の名前だけです。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーター (EE) では、変数の数値の別名をサポートするには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)特定のオブジェクトの別名を作成します。 別名を使用して検索[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)または[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)です。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次のメソッドが定義されている、`IDebugAlias`インターフェイスです。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|このエイリアスを参照するオブジェクトを取得します。|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|エイリアス名を取得します。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|取得、`ICorDebugValue`へのアクセスを提供するインターフェイスのマネージ コードについては、このオブジェクト (マネージ コードのみ) はします。|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|この使用されていないとエイリアスをマークします。|  
  
## <a name="remarks"></a>コメント  
 エイリアスは、後に # 文字、&#1001; などで文字列形式の 10 進数です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [式の評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)