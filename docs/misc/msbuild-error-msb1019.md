---
title: "MSBuild エラー MSB1019 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.InvalidLoggerError"
helpviewer_keywords: 
  - "MSB1019"
ms.assetid: 5d0169f7-f878-433a-ac30-d9d6010130af
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB1019
**Logger スイッチが正しく形成されませんでした。**  
  
 **\/logger** スイッチの指定が間違っています。  logger を指定するには、最低でも logger アセンブリを指定する必要があります。読み込む logger を明示的に指定する場合は、logger クラスと logger アセンブリの両方を指定する必要があります。  logger のパラメーターは省略可能です。  
  
### このエラーを解決するには  
  
1.  logger クラスおよび logger アセンブリの両方を使用して logger を指定します。  `<logger>` の構文は次のとおりです。  
  
     `<logger class>,<logger assembly>[;<logger parameters>]`  
  
     `<logger class>` の構文は次のとおりです。  
  
    ```  
    [<partial or full namespace>.]<logger class name>  
    ```  
  
     `<logger assembly>` の構文は次のとおりです。  
  
    ```  
    {<assembly name>[,<strong name>] | <assembly file>}  
    ```  
  
     `<logger parameters>` は省略可能であり、入力されたとおりに logger に渡されます。  
  
     例 : \/`logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`  
  
## 参照  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)   
 [ビルド ロガー](../msbuild/build-loggers.md)