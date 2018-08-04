---
title: ディレクトリを追加する、新しい項目 ダイアログ ボックスの追加 |Microsoft Docs
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
ms.openlocfilehash: ba535908b1c5ccb06f0f29490c0b87c377d6b2be
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498335"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>新しい項目の追加 ダイアログ ボックスにディレクトリを追加します。
次のコード例は、ディレクトリの新しいセットを登録する方法を示します、**新しい項目の追加** ダイアログ ボックス。 用のディレクトリ、**新しい項目の追加** ダイアログ ボックスは、プロジェクトごとに異なります。 そのため、下のディレクトリに登録されて、**プロジェクト**で見つかったサブキー **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**します。
  
## <a name="registry-script"></a>レジストリ スクリプト  
  
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
  
 `%Template_Path%`値をプロジェクト テンプレートを格納するディレクトリの完全なパスを指定します。 これらのテンプレートには、いずれかを指定できる *.vsz*ファイルまたは複製する典型的なテンプレート ファイル。  
  
 `SortPriority`値が並べ替えの優先順位を指定します。  
  
## <a name="add-items-to-an-existing-project"></a>既存のプロジェクトに項目を追加します。  
 既存のプロジェクトに項目を追加することもできます。 たとえば、[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]プロジェクトに項目を追加することができます、 *\<ルート > \Program Files\Microsoft Visual Studio\VC #\CSharpProjectItems\LocalProjectItems*フォルダー。 この場合、`%GUID_Project%`は c# プロジェクト ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}) の GUID です。  
  
 プロジェクト サブタイプをプログラミングによって既存のプロジェクトを拡張することもできます。 プロジェクト サブタイプの場合は、新しいプロジェクトの種類を記述することがなくプロジェクトを拡張できます。 プロジェクト サブタイプの詳細については、次を参照してください。[プロジェクトのサブタイプ](../../extensibility/internals/project-subtypes.md)します。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトと項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)   
 [新しい項目の追加 ダイアログ ボックスに項目の追加](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [[新しいプロジェクト] ダイアログ ボックスにディレクトリを追加します。](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)