---
title: IDebugApplicationNode インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7bd38a0fbbdd596f6a1f6bb040190dddca78bf9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348998"
---
# <a name="idebugapplicationnode-interface"></a>IDebugApplicationNode インターフェイス
`IDebugApplicationNode`インターフェイスの機能を拡張する、`IDebugDocumentProvider`インターフェイス プロジェクト ツリー内でコンテキストを提供しています。  
  
 継承されたメソッドだけでなく`IDebugDocumentProvider`、`IDebugApplicationNode`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|このアプリケーションのノードの子ノードを列挙します。|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|このアプリケーションのノードの親ノードを返します。|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|このアプリケーションのノードのドキュメント プロバイダーを設定します。|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|によりこのアプリケーションはすべての参照を解放し、非アクティブな状態を入力します。|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|指定されたプロジェクト ツリーには、このアプリケーションのノードを追加します。|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|プロジェクト ツリーからこのアプリケーションのノードを削除します。|