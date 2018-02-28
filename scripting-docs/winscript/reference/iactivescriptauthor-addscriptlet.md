---
title: "IActiveScriptAuthor::AddScriptlet |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b21f906a73a313bf775683ba63738adb25af0007
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
コード スクリプトレットをルート レベルの子として追加`IScriptNode`オブジェクト。 ホストでは、スクリプトレットの完全修飾名はのみに 2 つのレベルに許可されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszDefaultName`  
 [in]スクリプトレットに関連付ける既定の名前のアドレス。  
  
 `pszCode`  
 [in]スクリプトレット テキストのアドレス。  
  
 `pszItemName`  
 [in]ホストで完全修飾スクリプトレットの名前を最上位レベルの識別子のバッファーのアドレス。  
  
 `pszSubItemName`  
 [in]ホストで完全修飾スクリプトレットの名前の第 2 レベルの識別子のバッファーのアドレス。 名前に 1 つだけのレベルがある場合は、NULL に設定します。  
  
 `pszEventName`  
 [in]スクリプトレットは、イベント ハンドラーのイベント名を格納するバッファーのアドレス。  
  
 `pszDelimiter`  
 [in]最後のスクリプト ブロックの区切り記号のアドレス。 ときに`pszCode`解析は、テキストのストリームからホスト通常区切り文字を使用 (など、2 つ単一引用符)、スクリプト ブロックの終わりを検出します。 区切り記号が、スクリプト ブロックの末尾をマークしない場合は、このパラメーターを NULL に設定します。  
  
 `dwCookie`  
 [in]ホスト オブジェクトとスクリプトレットを関連付けるために使用するアプリケーション定義の値。  
  
 `dwFlags`  
 [in]使用しません。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)