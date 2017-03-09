---
title: "The custom tool &#39;custom tool&#39; failed. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.generator_fail_errorinfo"
ms.assetid: e846b946-a123-49fe-b4bc-a7bbda501417
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The custom tool &#39;custom tool&#39; failed. &lt;reason&gt;
カスタム ツールが正常に実行されていません。  
  
 n 層データセットを含むプロジェクトを更新したときに MSDataSetGenerator エラーが発生した場合は、すべてのプロジェクトを更新した後でカスタム ツールを再実行する必要があります。  
  
 カスタム ツール 'MSDataSetGenerator' が失敗しました。  \<データベース名\> の DataSetProject 属性に指定するプロジェクトは、現在のプロジェクトのバージョンと同じかそれ以降の .NET Framework のバージョンを対象とする必要があります。  
  
### n 層データセット内の MSDataSetGenerator エラーを修正するには  
  
-   ソリューション エクスプローラーで .xsd ファイルを右クリックし、**\[カスタム ツールの実行\]** をクリックします。