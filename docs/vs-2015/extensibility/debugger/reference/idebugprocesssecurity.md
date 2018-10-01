---
title: IDebugProcessSecurity |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c3cfa0d8ef0f43b21ec2057b71b688b2d3ecb66
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535526"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugProcessSecurity](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocesssecurity)します。  
  
`IDebugProcessSecurity` 安全なプロセスにアタッチがユーザーに警告するポートのサプライヤーによって実装されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProcessSecurity`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|ポート サプライヤーからユーザー名を取得します。|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|ユーザーに警告する、デバッグ プロセスにアタッチする安全ではありません。|  
  
## <a name="remarks"></a>Remarks  
 警告が表示し、ユーザーが接続しているプロセスは、安全でない考慮できる場合はキャンセルできるようにするには、このインターフェイスを実装します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [ポート](../../../extensibility/debugger/ports.md)   
 [ポート サプライヤー](../../../extensibility/debugger/port-suppliers.md)   
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

