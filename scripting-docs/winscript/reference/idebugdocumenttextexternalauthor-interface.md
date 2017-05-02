---
title: "IDebugDocumentTextExternalAuthor インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor インターフェイス"
ms.assetid: 0b04de1b-f922-4526-af4e-c0af2b7c1ce4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextExternalAuthor インターフェイス
安全にドキュメントを通知することによって、ファイル ベースのデバッガーのドキュメントを編集できるように外部エディター ソース ファイルが変更されたときの。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugDocumentTextExternalAuthor` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugDocumentTextExternalAuthor::GetPathName](../../winscript/reference/idebugdocumenttextexternalauthor-getpathname.md)|ドキュメントの完全パスとファイル名を返します。|  
|[IDebugDocumentTextExternalAuthor::GetFileName](../../winscript/reference/idebugdocumenttextexternalauthor-getfilename.md)|パス情報なしでドキュメントの名前を返します。|  
|[IDebugDocumentTextExternalAuthor::NotifyChanged](../../winscript/reference/idebugdocumenttextexternalauthor-notifychanged.md)|ドキュメント ソースが変更したことをホストに通知します。|