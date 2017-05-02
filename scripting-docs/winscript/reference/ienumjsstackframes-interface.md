---
title: "IEnumJsStackFrames インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumJsStackFrames インターフェイス
JavaScript の jscript9diag.dll でスタック アンワインドが可能になるようにデバッガーによって実装されます。  
  
## 構文  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## メンバー  
  
### パブリック メソッド  
  
|Name|Description|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next メソッド](../../winscript/reference/ienumjsstackframes-next-method.md)|指定した数のフレームを取得します。|  
|[IEnumJsStackFrames::Reset メソッド](../../winscript/reference/ienumjsstackframes-reset-method.md)|スタック フレームを最初の要素の前の位置にリセットします。|  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)