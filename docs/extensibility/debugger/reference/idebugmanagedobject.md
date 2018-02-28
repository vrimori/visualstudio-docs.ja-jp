---
title: "IDebugManagedObject |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e096d7c11e044f62f82fb8162aac5553e38b3a29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 このインターフェイスにより、式エバリュエーターを値クラスのインスタンスに対するプロパティまたはメソッドを呼び出すには、(EE) (たとえば、 `System.Decimal`) を呼び出さずに、値を設定して[評価](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)デバッグ中のプログラムにします。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugManagedObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターでは、変数などのマネージ コード オブジェクトを表すには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスを取得するには、呼び出す[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)上、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)を表す値クラスのインスタンス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 継承されたメソッドだけでなく[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)、`IDebugManagedObject`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|マネージ コード オブジェクトを表すし、適切なマネージ コードのインターフェイスを取得できるインターフェイスを返します。|  
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|指定したマネージ コード オブジェクトの値をこのオブジェクトの値を設定します。|  
  
## <a name="remarks"></a>コメント  
 式エバリュエーターでは、このインターフェイスを使用して、解析ツリーで、マネージ コード オブジェクトを格納します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [式の評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [評価します。](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)