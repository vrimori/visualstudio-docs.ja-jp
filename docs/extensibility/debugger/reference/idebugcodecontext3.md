---
title: "IDebugCodeContext3 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c7866b5a76be82e7cbfa04605ad5117a0b2a8fd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
拡張、 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)インターフェイス モジュールとプロセスのインターフェイスの取得を有効にします。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジンによって実装され、によって消費されている、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]デバッグ パッケージです。  
  
## <a name="methods"></a>メソッド  
 メソッドだけでなく、`IDebugCodeContext2`インターフェイス、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|デバッグ モジュールのインターフェイスへの参照を取得します。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|デバッグ プロセスのインターフェイスへの参照を取得します。|  
  
## <a name="remarks"></a>コメント  
 これは、一般に、実装する必要はありませんが、省略可能なインターフェイスです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll