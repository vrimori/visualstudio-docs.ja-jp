---
title: 新しいプロジェクト ダイアログ ボックスへのディレクトリの追加 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5c8686a34f52c7dc2e6c96b602811d7e12a6a7e6
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500788"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>[新しいプロジェクト] ダイアログ ボックスにディレクトリを追加します。
新しいプロジェクトの種類を作成するときに登録することもできますで新しいディレクトリを**新しいプロジェクト**ダイアログ ボックスを使用するためのテンプレートとして表示します。 次のコード例では、ノードとも呼ばれる、新しいディレクトリを登録する方法について説明します。 例で、VSPackage によって公開されているテンプレート*CLSID_Package*、登録されます。 その結果の左側にある、**新しいプロジェクト** ダイアログ ボックスによって決定された名と追加のノードを提供する、 *Folder_Label_ResID*リソース。 このリソースは、VSPackage のサテライト DLL から読み込まれます。  
  
 **フォルダー**値を下にあるフォルダーの GUID を表す、 *Folder_Label_ResID*ノードが表示されます。 例では、GUID を表す、**その他のプロジェクト**フォルダーに、**プロジェクトの種類**のウィンドウ、**新しいプロジェクト** ダイアログ ボックス。 場合、**その他のプロジェクト**値が存在しない場合、最上位レベルにラベルを配置します。  
  
 `TemplatesDir`値をプロジェクト テンプレートを格納するディレクトリの完全なパスを指定します。 これらのファイルには、いずれかを指定できる *.vsz*ファイルまたはクローンを作成する一般的なテンプレート ファイル。  
  
 指定した場合`TemplatesLocalizedSubDir`のサブディレクトリの名前を示す文字列のリソース ID があります`TemplatesDir`ローカライズされたテンプレートを保持しています。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]文字列リソース サテライト DLL から、いずれかがある各サテライト DLL 含めることができます別サブディレクトリの名前。 `SortPriority`値が並べ替えの優先順位を指定します。  
  
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
 [新しい項目の追加 ダイアログ ボックスに項目の追加](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [新しい項目の追加 ダイアログ ボックスにディレクトリを追加します。](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)