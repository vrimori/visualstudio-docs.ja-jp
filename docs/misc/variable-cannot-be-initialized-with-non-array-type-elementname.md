---
title: "変数を非配列型 &#39;&lt;elementname&gt;&#39; で初期化することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36536"
  - "bc36536"
helpviewer_keywords: 
  - "BC36536"
ms.assetid: 959415de-164e-4971-aab0-faad315753e9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 変数を非配列型 &#39;&lt;elementname&gt;&#39; で初期化することはできません
配列として宣言されている変数は、配列値で初期化する必要があります。  
  
```  
' Not valid. ' The following line causes this error when executed with Option Strict off. ' Dim arrayVar1() = 10  
```  
  
 **エラー ID:** BC36536  
  
### このエラーを解決するには  
  
-   配列値を使用して配列変数を初期化します。  
  
    ```  
    ' With Option Strict off. Dim arrayVar2() = {1, 2, 3} ' With Option Strict on. Dim arrayVar3() As Integer = {1, 2, 3}  
    ```  
  
## 参照  
 [NOTINBUILD 配列変数](http://msdn.microsoft.com/ja-jp/c2da78bd-6928-46ba-805f-44f819dfaf93)