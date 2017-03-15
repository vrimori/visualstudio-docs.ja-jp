---
title: "Configuration name is not valid. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INVALID_CFG_NAME"
  - "vs.message.0x800A00B7"
ms.assetid: aa439582-0863-41d3-825c-7c45b1773cde
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Configuration name is not valid.
このエラーが発生するのは一般的に、ビルド構成に入力された名前に、\<、\>、&#124;、\* などの無効な文字が含まれている場合です。  
  
### このエラーを解決するには  
  
1.  構成名に、\<、\>、\*、&#124;、:、\\、\/、&、%、"、.、\#、?、または文字列の先頭の空白や末尾の空白が含まれていないことを確認します。  さらに、構成名には、"nul"、"aux"、"con"、"com\#"、"lpt\#" など、Windows や DOS 用に予約された名前は使用できません。  
  
2.  名前を再入力します。  
  
## 参照  
 [Visual Studio でのアプリケーションのビルド](../ide/compiling-and-building-in-visual-studio.md)