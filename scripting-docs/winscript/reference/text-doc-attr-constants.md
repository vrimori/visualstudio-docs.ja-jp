---
title: "TEXT_DOC_ATTR 定数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: TEXT_DOC_ATTR
apilocation: scrobj.dll
helpviewer_keywords: 
  - "TEXT_DOC_ATTR 定数"
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# TEXT_DOC_ATTR 定数
ドキュメントの属性を記述します。  
  
## 構文  
  
```  
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## 定数  
  
|定数|値|説明|  
|--------|-------|--------|  
|TEXT\_DOC\_ATTR\_READONLY|0x00000001|ドキュメントは読み取り専用です。|  
|TEXT\_DOC\_ATTR\_TYPE\_PRIMARY|0x00000002|ドキュメントは、このドキュメント ツリーのプライマリ ファイルです。|  
|TEXT\_DOC\_ATTR\_TYPE\_WORKER|0x00000004|ドキュメントは、ワーカーです。|  
|TEXT\_DOC\_ATTR\_TYPE\_SCRIPT|0x00000008|ドキュメントは、スクリプト ファイルです。|  
  
## 参照  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)