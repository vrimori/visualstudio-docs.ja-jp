---
title: IDebugSyncOperation::InProgressAbort |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab8bae7f131d24c1a2c7272dc8d1178e12bf0e6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095525"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
別のスレッドで実行中の操作をキャンセルします。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>パラメーター  
 このメソッドには、パラメーターはありません。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|操作を取り消すことができません。|  
|`E_ABORT`|操作を完了できませんでした。|  
  
## <a name="remarks"></a>Remarks  
 プロセス デバッグ マネージャーは、別のスレッドで実行中の操作を中止するデバッガー スレッド内からは、このメソッドを呼び出します。  
  
 場合、`InProgressAbort`返しますメソッドは、操作を完了できません、`E_ABORT`できるだけ早くします。 このメソッドが返す`E_NOTIMPL`場合は、操作を取り消すことができません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSyncOperation インターフェイス](../../winscript/reference/idebugsyncoperation-interface.md)