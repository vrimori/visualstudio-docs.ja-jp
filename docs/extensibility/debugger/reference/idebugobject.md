---
title: "IDebugObject |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject
helpviewer_keywords: IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1122b427b6678d7f097d424aca0420642fecdbb2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 このインターフェイスは、シンボルと式の値をカプセル化する、バインダーを作成するオブジェクトを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターでは、オブジェクトを表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、式エバリュエーターが解析された式で使用するすべてのオブジェクトの基本クラスです。 呼び出しによって返される、[バインド](../../../extensibility/debugger/reference/idebugbinder-bind.md)メソッドです。 [QueryInterface](/cpp/atl/queryinterface)このインターフェイスより専門的なインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugObject`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|オブジェクトのサイズを取得します。|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|連続する一連のバイトとしてオブジェクトの値を取得します。|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|連続する一連のバイトからオブジェクトの値を設定します。|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|このオブジェクトの参照値を設定します。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|オブジェクトの値のアドレスを表すメモリ コンテキストを取得します。|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|デバッグ エンジンのアドレス空間には、管理対象のオブジェクトのコピーを作成します。|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|このオブジェクトが null 参照であるかどうかをテストします。|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|このオブジェクトを比較します。|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|このオブジェクトは読み取り専用のかどうかを判断します。|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|かどうか、オブジェクトは、透過プロキシを決定します。|  
  
## <a name="remarks"></a>コメント  
 式エバリュエーターでは、基底クラスとしてのこのインターフェイスを使用して、解析ツリー内のオブジェクトを表します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [式の評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [バインド](../../../extensibility/debugger/reference/idebugbinder-bind.md)