---
title: IDebugFirewallConfigurationCallback2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4b2aa5c4e45dbdf126a0144ebdfd9a0b102e170
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010286"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
要求に DCOM を使用するデバッグ エンジンを有効、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]ファイアウォールをリモート デバッグするブロックはしないことを確認するための UI。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 セッション デバッグ マネージャーのポート オブジェクトによって実装されます。  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDebugFirewallConfigurationCallback2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|ファイアウォール ブロックされていないことのリモート デバッグを要求します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll