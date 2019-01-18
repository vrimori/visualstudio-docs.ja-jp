---
title: IRemoteDebugApplicationThreadEx:EnumGlobalContexts |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThreadEx:EnumGlobalContexts
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationThreadEx:EnumGlobalContexts
ms.assetid: a6c0bc3f-4afc-41e1-b734-06e252c5b171
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5112ea59584544669b995d20490a1f01fac971ed
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347945"
---
# <a name="iremotedebugapplicationthreadexenumglobalcontexts"></a>IRemoteDebugApplicationThreadEx:EnumGlobalContexts
このスレッドで実行されているすべての言語用のグローバル式のコンテキストを列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT EnumGlobalExpressionContexts(  
   IEnumDebugExpressionContexts**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]このスレッドで実行されているすべての言語用のグローバル式のコンテキストを一覧する列挙子。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks