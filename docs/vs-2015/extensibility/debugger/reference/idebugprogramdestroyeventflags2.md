---
title: IDebugProgramDestroyEventFlags2 |Microsoft Docs
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
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d062fe93a18b88cd6c24e0ece18d30f186c6420f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777033"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

既定の動作をオーバーライドするデバッグ エンジンを有効、 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] UI のデバッグ セッションを終了するとします。  
  
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
 既定の動作、 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] UI は、すべてのプログラムには、プログラムが送信後に、デザイン モードに戻るにはイベントを破棄します。 このインターフェイスは、その動作を変更するデバッグ エンジンを使用します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll

