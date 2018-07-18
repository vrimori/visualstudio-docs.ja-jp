---
title: ディレクトリを追加する、新しい項目 ダイアログ ボックスを追加 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8d9989e8cf4ec8f0eb714a26e73d89fba339b71
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127749"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>ディレクトリを追加する、新しい項目 ダイアログ ボックスを追加
次のコード例は、ディレクトリの新しいセットを登録する方法を示します、**新しい項目の追加** ダイアログ ボックス。 用のディレクトリ、**新しい項目の追加** ダイアログ ボックスはプロジェクトごとに異なります。 見つかった、プロジェクトのサブキーの下で、ディレクトリが登録されているため、 \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
## <a name="the-registry-script"></a>レジストリ スクリプト  
  
```  
NoRemove Projects  
{  
  NoRemove %GUID_Project%  
  {  
    NoRemove AddItemTemplates  
    {  
      NoRemove TemplateDirs  
      {  
        ForceRemove %CLSID_Package%  
        {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
          {  
            val TemplatesDir = s '%Template_Path%'     
            val SortPriority = d 2000  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
 Template_Path 値では、プロジェクト テンプレートを格納するディレクトリの完全なパスを指定します。 これらのテンプレートには、.vsz ファイルまたは複製する典型的なテンプレート ファイルのいずれかを指定できます。  
  
 SortPriority 値は、並べ替えの優先順位を指定します。  
  
## <a name="adding-items-to-an-existing-project"></a>既存のプロジェクトに項目を追加します。  
 既存のプロジェクトに項目を追加することもできます。 たとえば、[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]プロジェクトに項目を追加することができます、\<ルート > \Program Files\Microsoft Visual Studio \VC#\CSharpProjectItems\LocalProjectItems フォルダーです。 この場合、 `%GUID_Project%` c# プロジェクト ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}) の GUID です。  
  
 プロジェクトのサブタイプをプログラミングで既存のプロジェクトを拡張することもできます。 プロジェクトのサブタイプでは、新しいプロジェクトの種類を記述することがなくプロジェクトを拡張できます。 プロジェクトのサブタイプの詳細については、次を参照してください。[プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)です。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトと項目テンプレートの登録](../../extensibility/internals/registering-project-and-item-templates.md)   
 [項目を追加する、新しい項目の追加 ダイアログ ボックス](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [[新しいプロジェクト] ダイアログ ボックスへの新しいディレクトリの追加](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)