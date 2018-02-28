---
title: "IActiveScriptAuthor::GetEventHandler |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b09f900162b6dba82696c946b53ab131691530c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
指定された属性を持つスクリプトレットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdisp`  
 [in]`IDispatch`オブジェクトに対応する、`NamedItem`スクリプトレットが関連付けられています。  
  
 `pszItem`  
 [in]ホストで完全修飾スクリプトレットの名前を最上位レベルの識別子のバッファーのアドレス。  
  
 `pszSubItem`  
 [in]ホストで完全修飾スクリプトレットの名前の第 2 レベルの識別子のバッファーのアドレス。 名前に 1 つだけのレベルがある場合は、NULL に設定します。  
  
 `pszEvent`  
 [in]イベントの名前を格納するバッファーのアドレス。 スクリプトレットは、このイベントのイベント ハンドラーです。  
  
 `ppse`  
 [out]ポインターを受け取る変数のアドレス、`IScriptEntry`を指定された属性を持つスクリプトレットのインターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)