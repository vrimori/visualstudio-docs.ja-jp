---
title: "IScriptNode::GetChild |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d127b1b8a8db0c6d272e50d33b523fbe182a9e21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
ノードに指定したインデックス位置にある子を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `isn`  
 [in]親の子のインデックス。  
  
 `ppsn`  
 [out]ポインターを受け取る変数のアドレス、`IScriptNode`子インスタンスのインターフェイスです。  
  
 `IScriptNode` Web ページを表すオブジェクトの場合は、このパラメーターは、スクリプト ブロックを格納しているオブジェクトを返します。  
  
 `IScriptEntry`スクリプト ブロックを指定するオブジェクトの場合は、このパラメーターは、関数を指定するオブジェクトを返します。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 `IScriptEntry`関数オブジェクトを指定するオブジェクトおよび`IScriptScriptlet`オブジェクトの子エントリがないために、このメソッドが失敗します。  
  
## <a name="see-also"></a>関連項目  
 [IScriptNode インターフェイス](../../winscript/reference/iscriptnode-interface.md)