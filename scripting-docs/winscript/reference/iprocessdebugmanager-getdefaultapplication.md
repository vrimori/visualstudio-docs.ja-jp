---
title: IProcessDebugManager::GetDefaultApplication |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.GetDefaultApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::GetDefaultApplication
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ae3b1bec5fc3aba6ad8e53343f929d133f05493
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091391"
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
現在のプロセスの既定のアプリケーション オブジェクトを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppda`  
 [out]このアプリケーションのデバッグ アプリケーション オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、新しいデバッグ アプリケーション オブジェクトを作成し、それを実行中に追加、必要に応じて、アプリケーションの一覧。  
  
 言語エンジンで指定されたアプリケーションを使用する必要があります、`GetDefaultApplication`メソッドをアプリケーションが用意されていないホストで実行されている場合。  
  
## <a name="see-also"></a>関連項目  
 [IProcessDebugManager インターフェイス](../../winscript/reference/iprocessdebugmanager-interface.md)