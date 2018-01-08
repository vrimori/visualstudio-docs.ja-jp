---
title: "原因となっている、新しい項目 ダイアログ ボックスを追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 923d95256a3ab0e63bdcf35c7ae38d70a117fa02
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>原因となっている、新しい項目 ダイアログ ボックスを追加
プロジェクトのサブタイプが項目の完全な新しいディレクトリを指定できます、**新しい項目の追加** ダイアログ ボックスを登録して**項目の追加**下のテンプレート、`Projects`レジストリ サブキー。  
  
## <a name="registering-add-new-item-templates"></a>登録する新しい項目の追加テンプレート  
 このセクションの内容が下にある**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects**レジストリにします。 以下のレジストリ エントリがあると、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]仮定プロジェクトのサブタイプを使用してプロジェクトを集計します。 エントリ、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトは、以下に示します。  
  
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
  
 `AddItemTemplates\TemplateDirs`サブキーにレジストリ エントリ項目箇所で使用可能なディレクトリへのパスにはが含まれています、**新しい項目の追加** ダイアログ ボックスを配置しています。  
  
 環境が自動的にすべてのロード、`AddItemTemplates`下にあるデータ、`Projects`レジストリ サブキー。 これには、基本プロジェクトの実装のためのデータと特定のプロジェクト サブタイプの型のデータを含めることができます。 各プロジェクトのサブタイプは、プロジェクトの種類によって識別される`GUID`です。 プロジェクトのサブタイプでは、代替セットのことを指定できます`Add Item`サポートすることにより、特定のフレーバー プロジェクト インスタンスのテンプレートを使用する必要があります、`VSHPROPID_ AddItemTemplatesGuid`から列挙<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>で<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>GUID を返す実装プロジェクトのサブタイプの値です。 場合`VSHPROPID_AddItemTemplatesGuid`プロパティが指定されていない、基本プロジェクトの GUID を使用します。  
  
 内の項目をフィルター処理することができます、**新しい項目の追加**を実装してダイアログ ボックス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>プロジェクト サブタイプ アグリゲーター オブジェクトのインターフェイスです。 たとえば、集計することによって、データベース プロジェクトを実装するプロジェクト サブタイプ、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトで、フィルター処理できます、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]から特定のアイテム、**新しい項目の追加** ダイアログ ボックスで、フィルター処理を実装することによってでは有効にする、追加できますプロジェクトの特定の項目をサポートすることによりデータベース`VSHPROPID_ AddItemTemplatesGuid`で<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>です。 詳細については、フィルター処理とする項目の追加、**新しい項目の追加**ダイアログ ボックスを参照してください[新しい項目の追加 ダイアログ ボックスに項目を追加する](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [プロジェクトの拡張に通常使用されるオブジェクトの CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)