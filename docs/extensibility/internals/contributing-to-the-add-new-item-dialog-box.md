---
title: "原因となっている、新しい項目] ダイアログ ボックスを追加 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原因となっている新しい項目の追加] ダイアログ ボックスを追加します"
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 原因となっている、新しい項目] ダイアログ ボックスを追加
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクトのサブタイプはENT0ENT \[出力\] ダイアログ ボックスに `Projects` のレジストリ キーの下に **項目の追加**  テンプレートの登録により項目の完全な新しいディレクトリを指定できます。  
  
## \[新しい項目テンプレートの登録  
 ここではレジストリの **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Projects** の下にあります。  レジストリ エントリは次のようなプロジェクトのサブタイプで集計する [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プロジェクトを前提としています。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プロジェクトのエントリを次に示します。  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 `AddItemTemplates\TemplateDirs` のサブ キーを実行する ENT0ENT \[出力\] ダイアログ ボックスで使用できるように項目を配置するディレクトリのパスを使用してレジストリ エントリが含まれます。  
  
 環境は `Projects` のレジストリ キーの下に自動的に `AddItemTemplates` のすべてのデータを読み込みます。  次の例は基本実装のプロジェクト データまたは特定のプロジェクトのサブタイプの型のデータを格納できます。  各プロジェクトのサブタイプはプロジェクトの種類 `GUID` で識別されます。  プロジェクトのサブタイプはプロジェクトのサブタイプ処理の GUID 値を返すための別の `Add Item` テンプレートを使用して風味が付けられているプロジェクト インスタンスに <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> の実装で <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> から `VSHPROPID_ AddItemTemplatesGuid` の列挙型のサポートで使用するように指定できます。  `VSHPROPID_AddItemTemplatesGuid` のプロパティが指定されていない場合基本プロジェクトの GUID が使用されます。  
  
 プロジェクトのサブタイプ アグリゲーターのオブジェクトの <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> インターフェイスの実装によって ENT0ENT \[出力\] ダイアログ ボックスの項目をフィルター処理できます。  たとえば[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プロジェクトを集計してデータベース プロジェクトを実行するにはプロジェクトのサブタイプはフィルター処理を実行してENT0ENT \[出力\] ダイアログ ボックスから [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の特定の項目をフィルター処理中に<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> の `VSHPROPID_ AddItemTemplatesGuid` をサポートしてデータベース プロジェクトの特定の項目を追加できます。  \[新しい項目の追加\] ダイアログ ボックスへの項目をフィルター処理し追加する方法の詳細については[項目を追加、新しい項目の追加\] ダイアログ ボックス](../Topic/Adding%20Items%20to%20the%20Add%20New%20Item%20Dialog%20Boxes.md) " " を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [通常、プロジェクトの拡張に使用されるオブジェクトの Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)