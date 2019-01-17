---
title: IEnumRemoteDebugApplicationThreads::Clone |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplicationThreads.Clone
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads::Clone
ms.assetid: d016e7cf-ae73-48ff-aee7-810222e0b05c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e64a83b9cf5184e8a7dfe45cc33b698e5bbdd4f6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091695"
---
# <a name="ienumremotedebugapplicationthreadsclone"></a>IEnumRemoteDebugApplicationThreads::Clone
現在の列挙子と同じ状態を格納する列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT Clone(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pperdat`  
 [out]返します、`IEnumRemoteDebugApplicationThreads`列挙子の複製のインターフェイス。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、現在の列挙子と同じ状態を格納する列挙子を作成します。  
  
## <a name="see-also"></a>関連項目  
 [IEnumRemoteDebugApplicationThreads インターフェイス](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)