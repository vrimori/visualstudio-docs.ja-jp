---
title: "IDebugDocumentTextEvents インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents インターフェイス"
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents インターフェイス
関連付けられたテキスト ドキュメントへの変更を示すイベントを提供します。  
  
> [!NOTE]
>  文書内のテキストは次のイベントが発生するとインターフェイスを変更します。  イベント ハンドラーは `IDebugDocumentText` のインターフェイスを使用して新しいテキストを取得することがあります。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugDocumentTextEvents` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|基になるドキュメントが破棄されたことを示し、無効です|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|新しいテキストでドキュメントに追加されたことを示しています|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|テキストが文書から削除されたことを示します。|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|テキストが置き換えられることを示します。|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|基になる文字位置の範囲に関連付けられたテキスト属性が変更されたことを示します。|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|ドキュメントの属性が変更されたことを示します。|