---
title: "IDebugPropertyEnumType_All インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75de35bd42ea91e7d27523ba42c392650686041a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertyenumtypeall-interface"></a>IDebugPropertyEnumType_All インターフェイス
`IDebugPropertyEnumType`インターフェイスが定義され、フィルターとして渡すことができますがの Iid の各`IDebugProperty::EnumMembers`適切な列挙子の要求中にします。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|名前を表すテキスト文字列を返します|  
  
 次のインターフェイスを継承`IDebugPropertyEnumType_All`、その他の方法はありません。  
  
```  
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)