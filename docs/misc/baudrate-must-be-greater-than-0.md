---
title: "BaudRate は 0 より大きくなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5d26c4b1-45ca-459b-9b96-907dbc6ea25c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# BaudRate は 0 より大きくなければなりません
`My.Computer.Ports.OpenSerialPort` メソッドに指定された `BaudRate` 引数は、0 より大きくなければなりません。  
  
### このエラーを解決するには  
  
-   `BaudRate` 引数の値を正の数値に変更します。  
  
## 参照  
 [My.Computer.Ports.OpenSerialPort メソッド](http://msdn.microsoft.com/ja-jp/ed1e75f0-635a-4229-8fe6-becea5d036c3)