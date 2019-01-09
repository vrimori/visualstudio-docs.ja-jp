---
title: IDebugSyncOperation::GetTargetThread |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.GetTargetThread
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::GetTargetThread
ms.assetid: e6eeeb90-b5ed-4727-8434-fa3186c25013
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4ff27e3d91abe19608bbe10051814d7e0f71af7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096708"
---
# <a name="idebugsyncoperationgettargetthread"></a>IDebugSyncOperation::GetTargetThread
この同期操作を行う対象のアプリケーションのスレッドを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetTargetThread(  
   IDebugApplicationThread**  ppatTarget  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppatTarget`  
 [out]この同期操作を行う対象のアプリケーション スレッドです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、この同期操作を行う対象のアプリケーションのスレッドを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSyncOperation インターフェイス](../../winscript/reference/idebugsyncoperation-interface.md)