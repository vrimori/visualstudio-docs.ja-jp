---
title: IDebugDocumentTextEvents インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bec89ae81d79fb7b0d822cafe2bf44f0ecd8ad81
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345660"
---
# <a name="idebugdocumenttextevents-interface"></a>IDebugDocumentTextEvents インターフェイス
関連付けられているテキスト ドキュメントへの変更を示すイベントを提供します。  
  
> [!NOTE]
>  ドキュメントのテキストは、このイベント インターフェイスを起動するときに変更します。 イベント ハンドラーを使用して新しいテキストを取得、`IDebugDocumentText`インターフェイス。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugDocumentTextEvents`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|基になるドキュメントが破棄され、が無効になっていることを示します|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|新しいテキストがドキュメントに追加されたことを示します|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|テキストがドキュメントから削除されたことを示します。|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|テキストが置き換えられることを示します。|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|基になる文字位置の範囲に関連付けられているテキストの属性が変更されたことを示します。|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|ドキュメントの属性が変更されたことを示します。|