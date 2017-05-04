---
title: "IDebugDocumentHost インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentHost インターフェイス"
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost インターフェイス
デバッガーに対して、ホスト固有の機能を、構文の色指定など、公開します。  `IDebugDocumentHelper::SetDebugDocumentHost` のメソッドは、引数としてこのインターフェイスを受け取ります。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugDocumentHost` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|`IDebugDocumentHelper::AddDeferredText`によって追加された元のホスト ドキュメントの文字範囲を返します。|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|ドキュメントのテキスト ブロックのテキスト属性を返します。|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|新しいドキュメントのコンテキストが作成されることが通知し、ホスト コントロール新しいコンテキストに応じてオブジェクトを返すことをホストできます。|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|ドキュメントのソース ファイルの完全パスとファイル名を含めて\) 返します。|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|パス情報なしでドキュメントの名前を返します。|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|ドキュメントのソース ファイルが保存されたこと、および内容が更新することをホストに通知します。|