---
title: "IDebugProgramEngines2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEngines2
helpviewer_keywords: IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 99ff94445caf60edde57f4365abbb5241d61127d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
このインターフェイスは、すべて使用可能なデバッグ エンジン (DE) このプログラムをデバッグできるを指定するプログラムのノードで使用します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramEngines2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 実装する同一のオブジェクトにこのインターフェイスを実装、DE やカスタム ポートのサプライヤー [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)特定プログラムを使用する特定の DE の確立をサポートするためにします。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、`IDebugProgramNode2`インターフェイスをこのインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProgramEngines2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|このプログラムをデバッグできるすべての可能な DEs を示します。|  
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|このプログラムのデバッグに使用する DE を選択します。|  
  
## <a name="remarks"></a>コメント  
 呼び出して、その選択が、[プログラム] ノードに登録されて、DE がユーザーによって選択されると、 [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)です。 選択されているエンジンが、エンジンによって返される[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)