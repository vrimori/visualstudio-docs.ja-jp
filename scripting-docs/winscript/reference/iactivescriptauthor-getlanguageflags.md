---
title: IActiveScriptAuthor::GetLanguageFlags |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6137f1cd77d2f305a9ff9d51ac49c214e4c4237b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645542"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
言語情報を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pgrfasa`  
 [out]言語情報が含まれているフラグ。 次の値の組み合わせが可能です。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|言語は、アプリケーションではなくエンジンを作成、スクリプトでスクリプトのイベント ハンドラーの作成を優先します。|  
|fasaSupportInternalHandler|0x0002|言語には、エンジンを作成するスクリプトによって作成されたスクリプトのイベント ハンドラーがサポートしています。|  
|fasaCaseSensitive|0x0004|スクリプト言語は大文字小文字を区別します。|  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 エンジンを作成するスクリプトは、イベント ハンドラーを管理している場合、アプリケーションを呼び出す必要があります`CreateChildHandler`から、`IScriptEntry`オブジェクト。 これを作成、`IScriptScriptlet`イベント ハンドラーに対応するオブジェクト。 エンジンは、スクリプトのエントリにも、イベント ハンドラーを追加します。 イベント ハンドラーは、指定の署名情報を含む空の関数です。  
  
 呼び出して、アプリケーションは、イベント ハンドラーを管理する場合、`CreateChildHandler`から、`IScriptNode`をイベント ハンドラー スクリプトレットを表すオブジェクト。 これを作成、`IScriptScriptlet`イベント ハンドラー スクリプトレットに関連付けられているオブジェクト。 アプリケーションがあります、イベントとして空の関数を追加するハンドラーを新規または既存の`IScriptEntry`オブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)