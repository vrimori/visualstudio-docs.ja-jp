---
title: "IActiveScriptAuthor::RemoveNamedItem |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.RemoveNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::RemoveNamedItem
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f3acc7d61d63ce4fb4fe53729ce43324b9718a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
削除、`NamedItem`エンジンを作成するスクリプトの名前空間のオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszName`  
 [in]識別するバッファーのアドレス、`NamedItem`削除するオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`S_FALSE`|`NamedItem`オブジェクトは、エンジンを作成するスクリプトの名前空間に存在することはありません。|  
  
## <a name="remarks"></a>コメント  
 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)を挿入するために使用、`NamedItem`オブジェクトをスクリプト エンジンの名前空間を作成します。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)