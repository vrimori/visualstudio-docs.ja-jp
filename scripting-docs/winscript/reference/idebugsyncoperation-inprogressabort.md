---
title: "IDebugSyncOperation::InProgressAbort |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugSyncOperation.InProgressAbort
apilocation: jscript.dll
helpviewer_keywords: IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df0b0ca1d775d4d99e1da5f88a207bd4f78f99b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
別のスレッドで実行中の操作をキャンセルします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>パラメーター  
 このメソッドには、パラメーターはありません。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|操作はキャンセルできません。|  
|`E_ABORT`|操作を完了できませんでした。|  
  
## <a name="remarks"></a>コメント  
 プロセスのデバッグ マネージャーは、別のスレッドで進行中の操作をキャンセルするデバッガー スレッド内からこのメソッドを呼び出します。  
  
 場合、`InProgressAbort`返しますメソッドは、操作を完了できません、`E_ABORT`できるだけ早くです。 このメソッドは返す`E_NOTIMPL`場合は、操作を取り消すことはできません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSyncOperation インターフェイス](../../winscript/reference/idebugsyncoperation-interface.md)