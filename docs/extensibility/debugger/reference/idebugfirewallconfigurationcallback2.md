---
title: IDebugFirewallConfigurationCallback2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1981d16141ed44ccbac0d2e05ae058451f0dff5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
DCOM を使用するように依頼するデバッグ エンジンを有効に、 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI をファイアウォールをリモート デバッグするブロックはしないことを確認してください。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 セッションのデバッグ マネージャーのポート オブジェクトによって実装されます。  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDebugFirewallConfigurationCallback2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|ファイアウォールをブロックしないことのリモート デバッグを要求します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll