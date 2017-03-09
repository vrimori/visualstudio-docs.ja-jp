---
title: "コンパイラの警告 (レベル 2) CS0444 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0444"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0444"
ms.assetid: 5beb8c06-39d3-4b59-a7c3-5590200bd43d
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS0444
定義済みの型 'type name 1' が 'System namespace 1' ではなく 'System namespace 2' で見つかりました  
  
 <xref:System.Int32> などの定義済みオブジェクトが、コンパイラが見つける必要のある場所ではなく、'System namespace 2' で見つかりました。  
  
 このエラーが発生する場合、.NET Framework が正しくインストールされていない可能性があります。 この問題を解決するには、.NET Framework を再インストールします。  
  
 基底クラス ライブラリを独自に作成している場合も、このエラーが発生する可能性があります。 この場合、エラーを解決するには、mscorlib をリビルドします。