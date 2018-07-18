---
title: IScriptNode::CreateChildHandler |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff2ba40d1570e23f0256bd34ca8aff0f8d77ce5c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729562"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
子インスタンスとして、スクリプトレットを追加、`IScriptNode`です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszDefaultName`  
 [in]スクリプトレットに関連付ける既定の名前のアドレス。  
  
 `prgpszNames`  
 [size_is で (`cpszNames`)]、ホスト上の完全修飾名から識別子の一覧です。  
  
 `cpszNames`  
 [in]識別子の数、`prgpszNames`パラメーター。  
  
 `pszEvent`  
 [in]スクリプトレットに関連付けられているイベント名を識別するバッファーのアドレス。  
  
 `pszDelimiter`  
 [in]最後のスクリプト ブロックの区切り記号のアドレス。 通常、ホストは、解析するため、スクリプト ブロックの終わりを検出するために (など、2 つ単一引用符)、区切り記号を使用します。  
  
 区切り記号は、エンジンを作成するスクリプトによって前処理を有効にします。 たとえば、エンジンでは、区切り記号として使用するための 2 つの単一引用符で単一引用符を置き換えることが。 エンジンは、区切り記号の使用方法を決定します。  
  
 スクリプト ブロックの末尾を識別する区切り記号を使用しない場合は、NULL に設定します。  
  
 `ptiSignature`  
 [in]関数オブジェクトの型情報。  
  
 `iMethodSignature`  
 [in]内の関数のインデックス、`ITypeInfo``ptiSignature`パラメーター。  
  
 `isn`  
 [in]親の子のインデックス。  
  
 `dwCookie`  
 [in]エントリをそのホスト オブジェクトを関連付けるために使用するアプリケーション定義の値。  
  
 `ppse`  
 [out]ポインターを受け取る変数のアドレス、`IScriptEntry`子インスタンスのインターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 スクリプトレットは、イベント ハンドラーを指定します。 呼び出された場合、このメソッドは、スクリプトレットを作成、 `IScriptNode` Web ページを表すオブジェクト。 このメソッドは、他のインターフェイスで呼び出された場合に成功しません。  
  
## <a name="see-also"></a>関連項目  
 [IScriptNode インターフェイス](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)