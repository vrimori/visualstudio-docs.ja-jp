---
title: "[新しいプロジェクト] ダイアログ ボックスにディレクトリを追加する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 881979b54fb8f8f07a7ffeb2f3648b690fe2bf78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>[新しいプロジェクト] ダイアログ ボックスにディレクトリを追加します。
新しいプロジェクトの種類を作成するときに登録することもできる、新しいディレクトリに、**新しいプロジェクト**ダイアログ ボックスを使用するためのテンプレートとして表示します。 次のコード例では、ノードとも呼ばれる、新しいディレクトリを登録する方法について説明します。 例では、VSPackage CLSID_Package によって公開されているテンプレートが登録されます。 その結果の左側にある、**新しいプロジェクト** ダイアログ ボックスは Folder_Label_ResID リソースによって決まります名、追加のノードを提供します。 このリソースは、VSPackage サテライト DLL から読み込まれます。  
  
 **フォルダー**値は Folder_Label_ResID ノードが表示されるフォルダーの GUID を表します。 例では、GUID を表します、**その他のプロジェクト**内のフォルダー、**プロジェクトの種類**のペイン、**新しいプロジェクト** ダイアログ ボックス。 場合、**その他のプロジェクト**値が存在しない場合、最上位レベルにラベルを配置します。  
  
 TemplatesDir 値では、プロジェクト テンプレートを格納するディレクトリの完全なパスを指定します。 これらのファイルには、.vsz ファイルまたはクローンを作成する一般的なテンプレート ファイルのいずれかを指定できます。  
  
 TemplatesLocalizedSubDir を指定する場合、ローカライズされたテンプレートを保持する TemplatesDir のサブディレクトリの名前を示す文字列のリソース ID があります。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]文字列リソースを読み込みますサテライト DLL からある場合、各サテライト DLL 含めることができます、異なるサブディレクトリ名にします。 SortPriority 値は、並べ替えの優先順位を指定します。  
  
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
  
## <a name="see-also"></a>参照  
 [プロジェクトと項目テンプレートの登録](../../extensibility/internals/registering-project-and-item-templates.md)   
 [項目を追加する、新しい項目の追加 ダイアログ ボックス](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [[新しい項目の追加] ダイアログ ボックスへの新しいディレクトリの追加](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)