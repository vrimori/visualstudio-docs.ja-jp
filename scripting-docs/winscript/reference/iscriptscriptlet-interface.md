---
title: "IScriptScriptlet インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3fa3253997d3a09a7170f3795bf8a7bbf8a182c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptscriptlet-interface"></a>IScriptScriptlet インターフェイス
実装するオブジェクト、`IScriptScriptlet`インターフェイスは、イベント ハンドラー スクリプトを表します。  
  
 継承されたメソッドだけでなく`IScriptEntry`、`IScriptScriptlet`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|スクリプトレットに関連付けられているイベントの名前を返します。|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|スクリプトレットに関連付けられている単純なイベント名を返します。 これは、任意の空白文字を含まない単一ワード名です。|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|スクリプトレットのオブジェクトのホストの完全修飾名の最後の識別子を返します。|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|スクリプトレットに関連付けられているイベントの名前を設定します。|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|スクリプトレットに関連付けられている単純なイベント名を設定します。 これは、任意の空白文字を含まない単一ワード名です。|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|スクリプトレットのオブジェクトのホストの完全修飾名の最後の識別子を設定します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト作成インターフェイス](../../winscript/reference/active-script-authoring-interfaces.md)