---
title: "TemplateGroupID 要素 (Visual Studio テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID"
helpviewer_keywords: 
  - "<TemplateGroupID> 要素 [Visual Studio テンプレート]"
  - "TemplateGroupID 要素 [Visual Studio テンプレート]"
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# TemplateGroupID 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

項目テンプレートを表示するプロジェクトの種類を指定します。  この要素は、[ShowByDefault \(Visual Studio テンプレート\)](../extensibility/showbydefault-visual-studio-templates.md) が `false` に設定されている場合、重要です。  [ShowByDefault \(Visual Studio テンプレート\)](../extensibility/showbydefault-visual-studio-templates.md) が `true` に設定されている場合、すべてのプロジェクトの種類で項目テンプレートを使用できます。  
  
## 構文  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|テンプレートをカテゴリに分類し、**\[新しいプロジェクト\]** ダイアログ ボックス、または **\[新しい項目の追加\]** ダイアログ ボックスでどのように表示させるかを定義します。|  
  
## テキスト値  
 テキスト値が必要です。  
  
 このテキストは、項目テンプレートのカテゴリの識別子を指定します。  
  
## 解説  
 `TemplateGroupID` は要素です。  
  
 `TemplateGroupID` 要素の値は、**\[新しい項目の追加\]** ダイアログ ボックスに表示されるテンプレートをフィルター処理するために、プロジェクト システム登録 \(HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<version number\>*\\Projects\\\) と共に使用されます。  
  
|Visual C\+\+ の値|説明|  
|---------------------|--------|  
|VC\-Native|ネイティブ プロジェクトに使用されます。  プロジェクトの種類を特定できない場合は、これが既定値になります。|  
|VC\-Managed|マネージ \(\/clr\) プロジェクトに使用されます|  
|VC\-Windows|Windows プラットフォーム \(ネイティブ\/マネージ\/ストア\) を対象とするすべてのプロジェクトに使用されます|  
|WinRT\-Native\-UAP|Windows 10 ストア プロジェクトに使用されます|  
|CodeSharing\-Native|共有済みの項目のプロジェクトに使用されます|  
|WinRT\-Native\-6.3|Windows 8.1 ストア プロジェクトに使用されます|  
|WinRT\-Native\-Phone\-6.3|Windows Phone 8.1 プロジェクトに使用されます|  
|WinRT \- ネイティブ|Windows 8.0 ストア プロジェクトに使用されます|  
|VC\-Android|Android プロジェクトに使用されます|  
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)