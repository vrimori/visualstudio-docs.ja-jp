---
title: "IScriptNode::createchildentry |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode. CreateChildEntry
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fcc010efe8fcf30a8f467dd94befff54bc5fac5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode::CreateChildEntry
子インスタンスを追加`IScriptEntry`です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `isn`  
 [in]親の子のインデックス。  
  
 `dwCookie`  
 [in]子エントリをそのホスト オブジェクトに関連付けるために使用するアプリケーション定義の値。  
  
 `pszDelimiter`  
 [in]最後のスクリプト ブロックの区切り記号のアドレス。 通常、ホストは、解析するため、スクリプト ブロックの終わりを検出するために (など、2 つ単一引用符)、区切り記号を使用します。  
  
 区切り記号は、前処理エンジンを作成するスクリプトを有効します。 たとえば、エンジンでは、区切り記号として使用するための 2 つの単一引用符で単一引用符を置き換えることが。 エンジンは、区切り記号の使用方法を決定します。  
  
 区切り記号が、スクリプト ブロックの末尾をマークしない場合は、NULL に設定します。  
  
 `ppse`  
 [out]ポインターを受け取る変数のアドレス、`IScriptEntry`子インスタンスのインターフェイスです。  
  
 `IScriptNode`このパラメーターは、Web ページを表すオブジェクトを返します、`IScriptEntry`インスタンスが、スクリプト ブロックを指定します。  
  
 `IScriptEntry`スクリプト ブロックを表すオブジェクトの場合は、このパラメーターを返します、`IScriptEntry`インスタンスが関数オブジェクトを指定します。  
  
 `IScriptEntry`関数を表すオブジェクトのオブジェクトをこのメソッドは失敗します。  
  
 `IScriptScriptlet`オブジェクトをこのメソッドは失敗します。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 `IScriptNode`インターフェイスは、Web ページまたはその要素を表します。 `IScriptEntry`インターフェイス (から派生した`IScriptNode`)、スクリプト ブロックまたは関数オブジェクトを表します。 `IScriptScriptlet`インターフェイス (から派生した`IScriptEntry`) イベント ハンドラーを表します。  
  
## <a name="see-also"></a>関連項目  
 [IScriptNode インターフェイス](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)