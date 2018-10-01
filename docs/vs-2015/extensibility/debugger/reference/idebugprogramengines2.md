---
title: IDebugProgramEngines2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3dc2e1af08e6668730e48956e184bfc3fad1d4a9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535293"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugProgramEngines2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramengines2)します。  
  
このインターフェイスは、使用可能なデバッグしたすべてのエンジン (DE) このプログラムをデバッグすることを指定するプログラムのノードによって使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramEngines2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 実装する同一のオブジェクトにこのインターフェイスを実装、DE またはカスタムのポート サプライヤー [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)特定のプログラムに使用する特定のドイツの確立をサポートするためにします。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)上、`IDebugProgramNode2`をこのインターフェイスを取得するインターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProgramEngines2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|このプログラムをデバッグできるすべての DEs を示します。|  
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|このプログラムのデバッグに使用するデバイスを選択します。|  
  
## <a name="remarks"></a>Remarks  
 呼び出すことで、[プログラム] ノードでその選択を登録、DE がユーザーによって選択されると、 [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)します。 選択されたエンジンが、エンジンによって返される[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)

