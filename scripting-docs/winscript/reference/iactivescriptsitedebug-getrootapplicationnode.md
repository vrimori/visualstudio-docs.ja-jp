---
title: IActiveScriptSiteDebug::GetRootApplicationNode |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetRootApplicationNode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetRootApplicationNode
ms.assetid: 2393f566-6b97-47c0-8041-4dd7e3b1d3a3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abcb7c307513e513f3ba4d3a64d34f1e07e60d74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724722"
---
# <a name="iactivescriptsitedebuggetrootapplicationnode"></a>IActiveScriptSiteDebug::GetRootApplicationNode
スクリプトでは、ドキュメントを追加するか、アプリケーション ノードを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRootApplicationNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppdanRoot`  
 [out]スクリプト ドキュメントを保持するデバッグ アプリケーション ノード。 指定できます`NULL`です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、スクリプト ドキュメントを追加する対象のアプリケーション ノードを返します。 メソッドが返すことができます`NULL`の`ppdanRoot`場合はスクリプト ドキュメントを最上位レベルにする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSiteDebug インターフェイス](../../winscript/reference/iactivescriptsitedebug-interface.md)