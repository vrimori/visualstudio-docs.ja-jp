---
title: "方法 : テンプレート内のパラメーターを置き換える | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テンプレート パラメーター, 代入"
  - "Visual Studio のテンプレート, 使用 (パラメーターを)"
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 方法 : テンプレート内のパラメーターを置き換える
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テンプレートに基づいてファイルを作成するとき、クラス名や名前空間などのテンプレート パラメーターを置き換えることができます。  テンプレート パラメーターの完全な一覧については、「[テンプレート名](../ide/template-parameters.md)」を参照してください。  
  
## プロシージャ  
 テンプレートに基づいてプロジェクトを作成するときは常に、そのテンプレートのファイル内のパラメーターを置き換えることができます。  この手順では、テンプレートを使用して新しいプロジェクトを作成するとき、名前空間の名前を安全なプロジェクト名に置き換えるテンプレートの作成方法について説明します。  
  
#### パラメーターを使用して名前空間の名前をプロジェクト名に置き換えるには  
  
1.  テンプレートの 1 つ以上のコード ファイルにパラメーターを挿入します。  例:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  テンプレート パラメーターは、$*parameter*$ という形式で記述します。  
  
2.  テンプレートの .vstemplate ファイルで、このファイルを含む `ProjectItem` 要素を検索します。  
  
3.  `ProjectItem` 要素の `ReplaceParameters` 属性を `true` に設定します。  例:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## 参照  
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [テンプレート名](../ide/template-parameters.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem 要素 \(Visual Studio 項目テンプレート\)](../extensibility/projectitem-element-visual-studio-item-templates.md)