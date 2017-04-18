---
title: "IDebugProgramHost2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
caps.latest.revision: 11
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
ms.openlocfilehash: e142f77d19f8ee7787d71d2fa3aa8138b01d47ae
ms.lasthandoff: 04/05/2017

---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
このインターフェイスは、プログラムのホスト (プロセス) の情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramHost2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジンでは、このインターフェイスを実装として、同じオブジェクトに対して、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイスは、ホスト プロセスに関する情報を提供します。 これは、省略可能なインターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、`IDebugProgram2`インターフェイスをこのインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProgramHost2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|タイトル、フレンドリ名、またはこのプログラムのホスト プロセスのファイル名を取得します。|  
|[含ま](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|このプログラムのホスト プロセスのプロセス id を取得します。|  
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|このプログラムのホスト プロセスが実行されているコンピューターの名前を取得します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
