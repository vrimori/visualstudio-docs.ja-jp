---
title: IEnumDebugExtendedPropertyInfo インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo interface
ms.assetid: 316d5aa7-c949-48fc-89c1-239f00566cae
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c46815ff1fadd359e3200223dfe9041b6089ad3b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728172"
---
# <a name="ienumdebugextendedpropertyinfo-interface"></a>IEnumDebugExtendedPropertyInfo インターフェイス
列挙`ExtendedDebugPropertyInfo`構造体。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumDebugExtendedPropertyInfo`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IEnumDebugExtendedPropertyInfo::Clone](../../winscript/reference/ienumdebugextendedpropertyinfo-clone.md)|現在の列挙子と同じ列挙の状態を含む列挙子を作成します。|  
|[IEnumDebugExtendedPropertyInfo::GetCount](../../winscript/reference/ienumdebugextendedpropertyinfo-getcount.md)|数を取得`ExtendedDebugPropertyInfo`構造体、列挙子にします。|  
|[IEnumDebugExtendedPropertyInfo::Next](../../winscript/reference/ienumdebugextendedpropertyinfo-next.md)|指定した数を取得`ExtendedDebugPropertyInfo`列挙のシーケンス内の構造体。|  
|[IEnumDebugExtendedPropertyInfo::Skip](../../winscript/reference/ienumdebugextendedpropertyinfo-skip.md)|指定した数のスキップ`ExtendedDebugPropertyInfo`列挙のシーケンス内の構造体。|  
|[IEnumDebugExtendedPropertyInfo::Reset](../../winscript/reference/ienumdebugextendedpropertyinfo-reset.md)|列挙のシーケンスを最初にリセットします。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: dbgprop.h  
  
## <a name="see-also"></a>関連項目  
 [ExtendedDebugPropertyInfo 構造体](../../winscript/reference/extendeddebugpropertyinfo-structure.md)