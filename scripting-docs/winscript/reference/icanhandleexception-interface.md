---
title: "ICanHandleException インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ICanHandleException インターフェイス"
ms.assetid: 32df7f81-557d-40cf-a844-06a6eaa292f3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ICanHandleException インターフェイス
スクリプト エンジンの呼び出し元は、どの例外を呼び出し元が処理するかを指定できるようにします。  
  
## メソッド  
 `IUnknown` から継承するメソッドに加え、`ICanHandleException` インターフェイスは次のメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[ICanHandleException::CanHandleException](../../winscript/reference/icanhandleexception-canhandleexception.md)|スクリプト エンジンの呼び出し元が指定された例外を処理できるかどうかを判定します。|