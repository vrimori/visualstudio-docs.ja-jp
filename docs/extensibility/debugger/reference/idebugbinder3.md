---
title: "IDebugBinder3 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 47df761681525fd0c1062ae3d84be61c388282e9
ms.lasthandoff: 04/05/2017

---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 このインターフェイスは、型、エイリアス、およびカスタム ビジュアライザー サービスへのアクセスを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジンでは、エイリアス、カスタム ビジュアライザー サービス、およびオブジェクトの種類の情報へのアクセスをサポートするためにこのインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)インターフェイスを使用してこのインターフェイスを取得する[QueryInterface](/cpp/atl/queryinterface)です。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 によって提供されるメソッドに加え、 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)インターフェイス、このインターフェイスは、次を実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|このオブジェクトがバインドされているメモリを表すメモリ オブジェクトを取得します。|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|このオブジェクト (ある場合)、関連付けられた例外を取得します|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|指定した名前、エイリアスを取得します|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|このオブジェクトのすべてのエイリアスの配列を取得します|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|このオブジェクトに関連付けられている引数の型の数を取得します。|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|このオブジェクトに関連付けられている引数の型の一覧を取得します。|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|ビジュアライザー サービスへのインターフェイスを取得します。|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|メモリ コンテキスト オブジェクトの場所または 64 ビット メモリ アドレスのいずれかに変換します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [式の評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
