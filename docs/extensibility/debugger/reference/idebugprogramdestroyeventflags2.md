---
title: "IDebugProgramDestroyEventFlags2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bee4fe04f22bd9afbff8e2d26ef9d699b0226241
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
既定の動作をオーバーライドするデバッグ エンジンを有効に、 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI デバッグ セッションを終了するとします。  
  
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
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|プログラムを取得するフラグを破棄します。|  
  
## <a name="remarks"></a>コメント  
 既定の動作、 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI がすべてのプログラムは、プログラムを送信した後に、デザイン モードに戻るにはイベントを破棄します。 このインターフェイスは、その動作を変更するデバッグ エンジンを使用します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll