---
title: "IDebugApplicationNode インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 110e04d1c990f1b22f9740d8118a47f485dd041e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode-interface"></a>IDebugApplicationNode インターフェイス
`IDebugApplicationNode`インターフェイスの機能を拡張する、`IDebugDocumentProvider`インターフェイス プロジェクト ツリー内でコンテキストを提供しています。  
  
 継承されたメソッドだけでなく`IDebugDocumentProvider`、`IDebugApplicationNode`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|このアプリケーション ノードの子ノードを列挙します。|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|このアプリケーション ノードの親ノードを返します。|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|このアプリケーション ノードのドキュメント プロバイダーを設定します。|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|によりこのアプリケーションはすべての参照を解放し、非アクティブな状態を入力します。|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|このアプリケーション ノードを指定されたプロジェクトのツリーに追加します。|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|プロジェクト ツリーからこのアプリケーション ノードを削除します。|