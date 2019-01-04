---
title: IDebugPort2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1be76132e263a95412810c9fd1c4ba7162af9a77
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876917"
---
# <a name="idebugport2"></a>IDebugPort2
このインターフェイスは、マシン上のデバッグ ポートを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 カスタム ポート サプライヤーは、マシン上のデバッグ ポートを表すためには、このインターフェイスを実装します。  
  
 実装する必要がありますもポートは、ポート イベントの送信をサポートする場合、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>インターフェイスをサポートするために、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>さらに提供するインターフェイス、 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)または[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)このインターフェイスは、要求されたポートを表すを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugPort2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|ポート名を返します。|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|ポートの識別子を返します。|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|(該当する場合)、ポートの作成に使用される要求を返します。|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|このポートのポート サプライヤーを返します。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|プロセスのプロセスの識別子を指定するには、インターフェイスを返します。|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|ポートで実行されているすべてのプロセスを列挙します。|  
  
## <a name="remarks"></a>Remarks  
 ローカル ポートは、すべてのプロセスと、ローカル コンピューターで実行されるプログラムへのアクセスを提供します。 その他のポートには、Windows CE ベースのデバイスにシリアル ケーブルで接続または DCOM 以外のコンピューターへのネットワーク接続を表すことができます。 `IDebugPort2`インターフェイスの名前と、ポートの識別子を検索して、ポートで実行されているすべてのプロセスを列挙に使用されます。 起動し、ポート上のプロセスを終了するための機能が実装されている、`IDebugPortEx2`インターフェイス。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)