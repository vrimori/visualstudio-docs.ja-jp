---
title: 原因となっている、新しい項目 ダイアログ ボックスの追加 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5fcbac8b9e26bcca5a588846c14972156761d5b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533248"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>[新しい項目の追加] ダイアログ ボックスへの投稿
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[新しい項目の追加 ダイアログ ボックスに貢献する](https://docs.microsoft.com/visualstudio/extensibility/internals/contributing-to-the-add-new-item-dialog-box)します。  
  
プロジェクト サブタイプの項目の完全な新しいディレクトリを指定できます、**新しい項目の追加**登録することによって、ダイアログ ボックス**項目の追加**下のテンプレート、`Projects`レジストリ サブキー。  
  
## <a name="registering-add-new-item-templates"></a>登録する新しい項目の追加テンプレート  
 このセクションでは、下にある**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects**レジストリにします。 以下のレジストリ エントリの想定を[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]プロジェクトは、架空のプロジェクト サブタイプによって集計されます。 エントリ、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]プロジェクトは、以下に示します。  
  
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
  
 `AddItemTemplates\TemplateDirs`サブキーには項目箇所で使用可能なディレクトリのパスを使用するレジストリ エントリが含まれています、**新しい項目の追加** ダイアログ ボックスが配置されます。  
  
 環境が自動的にすべてのロード、`AddItemTemplates`データの下に、`Projects`レジストリ サブキー。 これには、プロジェクトの基本実装のデータと特定のプロジェクト サブタイプの型のデータを含めることができます。 各プロジェクトのサブタイプは、プロジェクトの種類で識別される`GUID`します。 プロジェクトのサブタイプでは、代替が設定されるように指定できます`Add Item`フレーバー プロジェクトの特定のインスタンスをサポートすることで使用するテンプレート、`VSHPROPID_ AddItemTemplatesGuid`から列挙<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>で<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>GUID を返す実装プロジェクト サブタイプの値。 場合`VSHPROPID_AddItemTemplatesGuid`プロパティが指定されていない、基本プロジェクトの GUID を使用します。  
  
 内の項目をフィルター処理することができます、**新しい項目の追加**を実装してダイアログ ボックス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>プロジェクト サブタイプ アグリゲーター オブジェクトのインターフェイス。 集約することによって、データベース プロジェクトを実装するプロジェクト サブタイプなど、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]プロジェクトで、フィルター処理できます、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]から特定の項目、**新しい項目の追加**とフィルター処理を実装することで、ダイアログ ボックスで有効にする、追加することができます特定のプロジェクト項目をサポートすることによってデータベース`VSHPROPID_ AddItemTemplatesGuid`で<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>します。 フィルター処理およびに項目を追加の詳細については、**新しい項目の追加**ダイアログ ボックスを参照してください[に新しい項目の追加 ダイアログ ボックスの項目の追加](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [プロジェクトの拡張に通常使用されるオブジェクトの CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

