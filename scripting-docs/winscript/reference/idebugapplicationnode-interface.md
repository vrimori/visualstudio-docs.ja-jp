---
title: "IDebugApplicationNode インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode インターフェイス"
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugApplicationNode インターフェイス
`IDebugApplicationNode` のインターフェイスは、プロジェクト ツリー内のコンテキストを提供することで `IDebugDocumentProvider` のインターフェイスの機能を拡張します。  
  
 `IDebugDocumentProvider` から継承するメソッドに加え、`IDebugApplicationNode` インターフェイスは次のメソッドを公開します。  
  
## Vtable の順序でメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|このアプリケーション ノードの子ノードを列挙します。|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|このアプリケーションのノードの親ノードを返します。|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|このアプリケーション ノードのドキュメントのプロバイダーを設定します。|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|すべての参照を解放し、非アクティブ状態に入るこのアプリケーションが発生します。|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|指定したプロジェクト ツリーにこのアプリケーションのノードを追加します。|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|プロジェクト ツリーからこのアプリケーション ノードを削除します。|