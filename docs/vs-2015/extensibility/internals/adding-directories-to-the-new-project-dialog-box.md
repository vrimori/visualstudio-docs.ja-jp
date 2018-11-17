---
title: 新しいプロジェクト ダイアログ ボックスへのディレクトリの追加 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a03e61cf3699cd45a7b4b8e6a7e5b7d192ca6de
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769744"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>[新しいプロジェクト] ダイアログ ボックスへの新しいディレクトリの追加
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

新しいプロジェクトの種類を作成するときに登録することもできますで新しいディレクトリを**新しいプロジェクト**ダイアログ ボックスを使用するためのテンプレートとして表示します。 次のコード例では、ノードとも呼ばれる、新しいディレクトリを登録する方法について説明します。 例では、VSPackage CLSID_Package によって公開されているテンプレートが登録されます。 その結果の左側にある、**新しいプロジェクト** ダイアログ ボックスでは、Folder_Label_ResID リソースによって決定された名と追加のノードが提供しています。 このリソースは、VSPackage のサテライト DLL から読み込まれます。  
  
 **フォルダー** Folder_Label_ResID ノードが表示されるフォルダーの GUID を表す値。 例では、GUID を表す、**その他のプロジェクト**フォルダーに、**プロジェクトの種類**のウィンドウ、**新しいプロジェクト** ダイアログ ボックス。 場合、**その他のプロジェクト**値が存在しない場合、最上位レベルにラベルを配置します。  
  
 TemplatesDir 値では、プロジェクト テンプレートを格納するディレクトリの完全なパスを指定します。 これらのファイルには、.vsz ファイルまたはクローンを作成する一般的なテンプレート ファイルのいずれかを指定できます。  
  
 TemplatesLocalizedSubDir を指定する場合、ローカライズされたテンプレートを保持する TemplatesDir のサブディレクトリの名前を示す文字列のリソース ID があります。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]文字列リソース サテライト DLL から、いずれかがある各サテライト DLL 含めることができます別サブディレクトリの名前。 SortPriority 値では、並べ替えの優先順位を指定します。  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトと項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)   
 [項目を追加、新しい項目の追加 ダイアログ ボックス](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [[新しい項目の追加] ダイアログ ボックスへの新しいディレクトリの追加](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

