---
title: "ウィザードでサポートされる入れ子のプロジェクト | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "項目の作成ウィザードを追加します。"
  - "入れ子になったプロジェクトでは、ウィザードのサポート"
  - "新しいプロジェクト ウィザード"
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# ウィザードでサポートされる入れ子のプロジェクト
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IDE では入れ子になったプロジェクトの親プロジェクトを実行できる 2 種類のウィザードを実行します :  **新しいプロジェクト**  ウィザードと  **項目の追加**  ウィザード。  
  
 ユーザーが \[ファイル\] メニューの \[ENT1ENT\] を選択すると ENT3ENT \[\] をクリックするかソリューション エクスプローラーの  **新しいプロジェクト**  を ENT5ENT \[\] を選択し右クリックして  **新しいプロジェクト**  ウィザードを起動するとIDE の **AddProject** のコマンドを実行し親プロジェクトの **AddProject** のコマンドの実装ではテンプレートのプロジェクト ファイルまたは一連のコンテキスト パラメーターを持つウィザード .vsz ファイル \(\) を返します。  
  
 同様に親プロジェクトの **AddItem** ウィザードの実装ではコンテキスト パラメーターのセットを持つ .vsz ファイルを返します。  
  
 ウィザードの詳細については[ウィザード \(します。Vsz\) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)[コンテキスト パラメーター](../../extensibility/internals/context-parameters.md) と [プロジェクトおよび項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md) を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [入れ子のプロジェクト](../../extensibility/internals/nesting-projects.md)