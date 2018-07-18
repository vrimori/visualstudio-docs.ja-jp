---
title: IScriptNode インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 788be3fe9cb5ba529e3d1ca653d4f0f5c35b5932
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733782"
---
# <a name="iscriptnode-interface"></a>IScriptNode インターフェイス
実装するオブジェクト、`IScriptNode`インターフェイスが Web ページを表します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IScriptNode`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|オブジェクトがアクティブであるかどうかを示します。|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|子インスタンスを追加`IScriptEntry`です。|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|子インスタンスとして、スクリプトレットを追加、`IScriptNode`です。|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|オブジェクト ツリーを削除します。|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|ノードに指定したインデックス位置にある子を返します。|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|ホスト オブジェクトとスクリプトレットを関連付けるために使用するアプリケーション定義の値を返します。|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|親の子の一覧で、オブジェクトのインデックスを返します。|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|現在のスクリプトのノードで使用されるスクリプト言語を返します。|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|子ノードの数を返します、`IScriptNode`オブジェクト。|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|返します、`IScriptNode`オブジェクトの親であるオブジェクト。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト作成インターフェイス](../../winscript/reference/active-script-authoring-interfaces.md)