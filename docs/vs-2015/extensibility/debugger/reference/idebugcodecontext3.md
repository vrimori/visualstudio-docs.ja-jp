---
title: IDebugCodeContext3 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc3ed9762a781b26c6bf12e0c51fa95efaf9056b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294997"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

拡張、 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)モジュールとプロセスのインターフェイスの取得を有効にするインターフェイス。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジンによって実装されで使用される、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]パッケージのデバッグ。  
  
## <a name="methods"></a>メソッド  
 メソッドだけでなく、`IDebugCodeContext2`インターフェイスでは、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|デバッグ モジュールのインターフェイスへの参照を取得します。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|デバッグ プロセスのインターフェイスへの参照を取得します。|  
  
## <a name="remarks"></a>Remarks  
 これは、一般に、実装する必要はありませんが、省略可能なインターフェイスです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll

