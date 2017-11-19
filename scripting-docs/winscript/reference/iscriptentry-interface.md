---
title: "IScriptEntry インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a785be8777cf3400f7723c24f1022bad6e22e330
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentry-interface"></a>IScriptEntry インターフェイス
実装するオブジェクト、`IScriptEntry`インターフェイスは、スクリプト ブロックまたは関数オブジェクトを表します。  
  
 継承されたメソッドだけでなく`IScriptNode`、`IScriptEntry`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|本文に対応するテキストを返します、`IScriptEntry`スクリプト ブロック、関数のブロック、またはスクリプトレットです。|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|識別する項目名を返します、`IScriptEntry`オブジェクト。|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|(関数) などの 1 つのオブジェクトを表すエントリに、オブジェクトの名前を返します。|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|開始位置とエントリの長さを返します。|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|タイプの情報を返す、`IScriptEntry`関数オブジェクト。|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|対応するテキストを返します、`IScriptEntry`スクリプト ブロック、またはソース コードに含まれている、`IScriptScriptlet`イベント ハンドラー。|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|本文内にあるテキストを設定、`IScriptEntry`スクリプト ブロックまたは`IScriptScriptlet`スクリプトレットです。|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|識別する項目の名前を設定、`IScriptEntry`オブジェクト。|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|(関数) などの 1 つのオブジェクトを表すエントリに、オブジェクトの名前を設定します。|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|型の情報を設定、`IScriptEntry`関数オブジェクト。|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|対応するテキストを設定、`IScriptEntry`スクリプト ブロック、またはソース コードに含まれている、`IScriptScriptlet`イベント ハンドラー。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト作成インターフェイス](../../winscript/reference/active-script-authoring-interfaces.md)