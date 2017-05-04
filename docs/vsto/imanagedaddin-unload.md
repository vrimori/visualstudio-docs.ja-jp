---
title: "IManagedAddin::Unload | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Unload メソッド"
  - "IManagedAddin::Unload"
ms.assetid: 40a73f07-2605-4745-8ac5-0a0189167fd7
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# IManagedAddin::Unload
  管理対象の VSTO アドインがアンロードされる直前に呼び出されます。  
  
## 構文  
  
```  
HRESULT Unload();  
```  
  
## 戻り値  
 メソッドが正常に完了したかどうかを示す HRESULT 値。  
  
## 解説  
 このメソッドは、Microsoft Office の現在のバージョンでは呼び出されません。 このメソッドは将来使用するために予約されています。  
  
## 参照  
 [IManagedAddin インターフェイス](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
  
  