---
title: IActiveScriptAuthor::AddScriptlet |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62499afe87a3d7dae31e609c9ce88f41e9d993a9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089213"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
コード スクリプトレットをルート レベルの子として追加`IScriptNode`オブジェクト。 ホストでは、スクリプトレットの完全修飾名をレベルが 2 つだけ許可されます。  
  
## <a name="syntax"></a>構文  
  
```cpp
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
 [in]ホストでスクリプトレットの完全修飾の名前の最上位レベルの識別子のバッファーのアドレス。  
  
 `pszSubItemName`  
 [in]ホストでスクリプトレットの完全修飾の名前の 2 番目のレベルの識別子のバッファーのアドレス。 名前に 1 つだけのレベルがある場合は NULL に設定します。  
  
 `pszEventName`  
 [in]スクリプトレットがイベント ハンドラーであるイベントの名前を格納するバッファーのアドレス。  
  
 `pszDelimiter`  
 [in]最後のスクリプト ブロックの区切り記号のアドレス。 ときに`pszCode`解析は、テキストのストリームからホスト通常 (など、2 つ単一引用符)、区切り記号を使用して、スクリプト ブロックの終了を検出します。 区切り記号がスクリプト ブロックの末尾をマークしない場合は、このパラメーターを NULL に設定します。  
  
 `dwCookie`  
 [in]ホスト オブジェクトとスクリプトレットを関連付けるために使用するアプリケーション定義の値。  
  
 `dwFlags`  
 [in]使用されません。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)