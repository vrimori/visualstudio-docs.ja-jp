---
title: IEnumDebugObjects |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 99c6c7a98074753e9ee7e1364adb35e1cdba9700
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 このインターフェイスを実装するオブジェクトのコレクションを表します、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)インターフェイスです。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターを実装するオブジェクトのセットを指定するには、このインターフェイスを実装する、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)インターフェイスです。 存在するための標準の COM 列挙ではないことに注意してください、 [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)メソッドです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|次のセットを取得[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)列挙体からのオブジェクト。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|指定されたエントリ数をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|最初のエントリを列挙型をリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|現在の列挙型のコピーを取得します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|列挙体のエントリの数を取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、配列内のオブジェクトのセットを列挙するデバッグ エンジンをできます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)