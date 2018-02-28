---
title: "IDebugDocumentTextEvents インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 078cd468b64d30c20f48a3392aa4509ed054fc3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextevents-interface"></a>IDebugDocumentTextEvents インターフェイス
関連付けられているテキスト ドキュメントへの変更を示すイベントを提供します。  
  
> [!NOTE]
>  このイベント インターフェイスの起動時にドキュメントのテキストを変更します。 イベント ハンドラーを使用して新しいテキストを取得することがあります、`IDebugDocumentText`インターフェイスです。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugDocumentTextEvents`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|基になるドキュメントが破棄されたことを示しますは無効になりました|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|新しいテキストがドキュメントに追加されたことを示します|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|テキストがドキュメントから削除されたことを示します。|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|テキストが置き換えられたことを示します。|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|基になる文字の位置の範囲に関連付けられているテキスト属性が変更されたことを示します。|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|ドキュメントの属性が変更されたことを示します。|