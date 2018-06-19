---
title: IEnumDebugPropertyInfo インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugPropertyInfo interface
ms.assetid: c5eea4da-8414-408a-a8f6-6a9ca8745868
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61504d60ccb59a0632376bf8e1ef762382b06326
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728232"
---
# <a name="ienumdebugpropertyinfo-interface"></a>IEnumDebugPropertyInfo インターフェイス
列挙`DebugPropertyInfo`構造体。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumDebugPropertyInfo`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|指定した数を取得`DebugPropertyInfo`列挙のシーケンス内の構造体。|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|指定した数のスキップ`DebugPropertyInfo`列挙のシーケンス内の構造体。|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|列挙のシーケンスを最初にリセットします。|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|現在の列挙子と同じ列挙の状態を含む列挙子を作成します。|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|数を取得`DebugPropertyInfo`構造体、列挙子にします。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: dbgprop.h  
  
## <a name="see-also"></a>関連項目  
 [DebugPropertyInfo 構造体](../../winscript/reference/debugpropertyinfo-structure.md)