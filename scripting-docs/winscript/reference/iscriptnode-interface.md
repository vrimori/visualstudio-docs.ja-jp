---
title: "IScriptNode インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptNode インターフェイス"
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IScriptNode インターフェイス
インターフェイスの実装が `IScriptNode` Web ページを表すオブジェクト。  
  
 `IUnknown` から継承するメソッドに加え、`IScriptNode` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|オブジェクトがまだアクティブかどうかを示します。|  
|[IScriptNode::CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|`IScriptEntry`の子インスタンスを追加します。|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|`IScriptNode`の子のインスタンスとしてスクリプトレットを追加します。|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|オブジェクト ツリーを削除します。|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|ノードの指定したインデックス位置にある子を返します。|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|ホスト オブジェクトとスクリプトレットを関連付けるためのアプリケーション定義の値を返します。|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|親の子リスト オブジェクトのインデックスを返します。|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|現在のスクリプトのノードで使用されるスクリプト言語を返します。|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|`IScriptNode` オブジェクトの子ノードの数を返します。|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|オブジェクトの親である `IScriptNode` のオブジェクトを返します。|  
  
## 参照  
 [アクティブ スクリプト作成インターフェイス](../../winscript/reference/active-script-authoring-interfaces.md)