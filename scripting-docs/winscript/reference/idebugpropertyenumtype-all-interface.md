---
title: "IDebugPropertyEnumType_All インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugPropertyEnumType_All
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugPropertyEnumType_All インターフェイス"
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPropertyEnumType_All インターフェイス
`IDebugPropertyEnumType` のインターフェイスは、適切な列挙子を要求している間の IID それぞれが `IDebugProperty::EnumMembers` にフィルターとして渡すことができるように定義されています。  
  
## 構文  
  
```  
IDebugPropertyEnumType_All : IUnknown  
```  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugPropertyEnumType\_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|名前を示す文字列を返します|  
  
 次のインターフェイスは `IDebugPropertyEnumType_All`から継承し、追加のメソッドはありません。  
  
```  
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## 参照  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)