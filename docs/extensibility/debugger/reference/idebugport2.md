---
title: "IDebugPort2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPort2
helpviewer_keywords: IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b40a141b90489fa65ffc5f29b363d3d647ca4cb8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugport2"></a>IDebugPort2
このインターフェイスは、コンピューター上のデバッグ ポートを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 カスタム ポート仕入先では、コンピューター上のデバッグ ポートを表すためには、このインターフェイスを実装します。  
  
 実装する必要がありますもポートは、送信ポート イベントをサポートする場合、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>をサポートするインターフェイス、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>をさらに提供するインターフェイス、 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)インターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)または[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)このインターフェイスは、要求されたポートを表すを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugPort2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|ポートの名前を返します。|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|ポートの識別子を返します。|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|(該当する場合)、ポートの作成に使用される要求を返します。|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|このポートのポートのサプライヤーを返します。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|プロセスのプロセスの識別子を指定するには、インターフェイスを返します。|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|ポートで実行されているすべてのプロセスを列挙します。|  
  
## <a name="remarks"></a>コメント  
 ローカル ポートは、すべてのプロセスと、ローカル コンピューターで実行中のプログラムへのアクセスを提供します。 Windows CE ベースのデバイスへの接続をシリアル ケーブルまたはネットワーク コンピューターへの接続は DCOM 以外、他のポートを表す場合があります。 `IDebugPort2`名前と識別子、ポートの列挙、ポートで実行されているすべてのプロセスを検索して起動すると、ポート上のプロセスを終了して機能を提供するインターフェイスを使用します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)