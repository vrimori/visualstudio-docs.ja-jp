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
ms.workload: vssdk
ms.openlocfilehash: 364b7d1480449601b211e5ac1736d0d85a87da5d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll