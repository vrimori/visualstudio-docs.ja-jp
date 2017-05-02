---
title: "IScriptEntry インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptEntry インターフェイス"
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry インターフェイス
インターフェイスの実装が `IScriptEntry` スクリプト ブロックまたは関数オブジェクト表すオブジェクト。  
  
 `IScriptNode` から継承するメソッドに加え、`IScriptEntry` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|`IScriptEntry` のスクリプト ブロック、ブロック、関数またはスクリプトレットの本体に対応するテキストを返します。|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|`IScriptEntry` のオブジェクトを識別する項目の名前を返します。|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|一つのオブジェクトを表すエントリ \(関数など\)、オブジェクトの名前。|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|エントリの開始位置と長さを返します。|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|`IScriptEntry` の関数オブジェクトの型情報を返します。|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|`IScriptEntry` のスクリプト ブロックに対応する、または `IScriptScriptlet` のイベント ハンドラーに含まれるソース・コードをテキストを返します。|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|`IScriptEntry` のスクリプト ブロックまたは `IScriptScriptlet` のスクリプトレットの本体にあるテキストを設定します。|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|`IScriptEntry` のオブジェクトを識別する項目の名前を設定します。|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|一つのオブジェクトを表すエントリ \(関数など\)、オブジェクトの名前。|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|`IScriptEntry` 関数オブジェクトのセットに情報を入力します。|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|`IScriptEntry` のスクリプト ブロックに対応する、または `IScriptScriptlet` のイベント ハンドラーに含まれるソース・コードをテキストを設定します。|  
  
## 参照  
 [アクティブ スクリプト作成インターフェイス](../../winscript/reference/active-script-authoring-interfaces.md)