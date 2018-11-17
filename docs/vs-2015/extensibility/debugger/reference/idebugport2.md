---
title: IDebugPort2 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6a3cdbc39ec3575f34e415aa9bbf2e371c66e68
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800212"
---
# <a name="idebugport2"></a>IDebugPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 ローカル ポートは、すべてのプロセスと、ローカル コンピューターで実行されるプログラムへのアクセスを提供します。 その他のポートには、Windows CE ベースのデバイスにシリアル ケーブルで接続または DCOM 以外のコンピューターへのネットワーク接続を表すことができます。 `IDebugPort2`インターフェイスを使用した名前と識別子、ポートの列挙、ポートで実行されているすべてのプロセスを検索しを起動すると、ポート上のプロセスを終了して機能を提供します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)

