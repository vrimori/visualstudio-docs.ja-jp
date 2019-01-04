---
title: IDebugProgramDestroyEventFlags2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3d0385af4ec795608672d8d7cbdb4b188246dea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825855"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
既定の動作をオーバーライドするデバッグ エンジンを有効、 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI のデバッグ セッションを終了するとします。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、デバッグ エンジンによって実装されます。 ホストを作成し、プロセスの有効期間にわたって複数のプログラムを破棄すると便利です。  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDebugProgramDestroyEventFlags2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|プログラムの取得フラグを破棄します。|  
  
## <a name="remarks"></a>Remarks  
 既定の動作、 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI は、すべてのプログラムには、プログラムが送信後に、デザイン モードに戻るにはイベントを破棄します。 このインターフェイスは、その動作を変更するデバッグ エンジンを使用します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll