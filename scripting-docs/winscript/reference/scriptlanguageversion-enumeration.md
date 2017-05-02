---
title: "SCRIPTLANGUAGEVERSION 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTLANGUAGEVERSION 列挙型
可能なスクリプト バージョンを指定します。  
  
## 構文  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION  
{  
    SCRIPTLANGUAGEVERSION_DEFAULT = 0,  
    SCRIPTLANGUAGEVERSION_5_7  = 1,  
    SCRIPTLANGUAGEVERSION_5_8  = 2,  
    SCRIPTLANGUAGEVERSION_MAX  = 255  
} SCRIPTLANGUAGEVERSION ;  
  
```  
  
## 列挙値  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION\_DEFAULT|既定のバージョン。  整数値は 0 です。|  
|SCRIPTLANGUAGEVERSION\_5\_7|バージョン 5.7 のスクリプト ウィンドウ。  整数値は 1.です。|  
|SCRIPTLANGUAGEVERSION\_5\_8|バージョン 5.8 のスクリプト ウィンドウ。  整数値は 2.です。|  
|SCRIPTLANGUAGEVERSION\_MAX|最大のバージョン。  整数値は 255 です。|  
  
## 参照  
 [アクティブ スクリプトの定数、列挙型、およびエラー コード](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)