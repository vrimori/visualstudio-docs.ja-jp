---
title: "IDebugProperty インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2888a6d781ecd501128545e483971a47859d9cda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugproperty-interface"></a>IDebugProperty インターフェイス
階層があるプロパティ デバッグされているエンティティの名前、型、および値の記述に使用します。 ほとんどの場合、`IDebugProperty`式の評価、ステートメントの評価、またはレジスタ評価の結果を表すために使用します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表のメソッドを示しています、`IDebugProperty`インターフェイスです。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|取得、`DebugPropertyInfo`これを説明します。`IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|プロパティに拡張された情報を取得します。|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|文字列からのプロパティの値を設定します。|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|プロパティのメンバーを列挙します。|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|プロパティの親を取得します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: dbgprop.h