---
title: "ディレクトリを追加する、新しい項目] ダイアログ ボックスを追加 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[新しい項目] ダイアログ ボックスを追加の拡張"
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# ディレクトリを追加する、新しい項目] ダイアログ ボックスを追加
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次のコード例では、ディレクトリの新しいセットを登録、 **新しい項目の追加** ] ダイアログ ボックス。 ディレクトリを **新しい項目の追加** ] ダイアログ ボックスはプロジェクトごとに異なります。 そのため、ディレクトリは、\< HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects > に、プロジェクトのサブキーの下で登録されます。  
  
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
  
 Template_Path 値では、プロジェクト テンプレートを格納するディレクトリの完全なパスを指定します。 これらのテンプレートには、.vsz ファイルまたはクローンを作成する典型的なテンプレート ファイルのいずれかを指定できます。  
  
 SortPriority 値では、並べ替えの優先順位を指定します。  
  
## <a name="adding-items-to-an-existing-project"></a>既存のプロジェクトに項目を追加します。  
 既存のプロジェクトに項目を追加することもできます。 たとえば、 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] プロジェクトに項目を追加することができます、\< ルート>\Program Files\Microsoft Visual Studio \VC#\CSharpProjectItems\LocalProjectItems フォルダーです。 この場合、 `%GUID_Project%` c# プロジェクト ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}) の guid を指定します。  
  
 プロジェクトのサブタイプをプログラミングして、既存のプロジェクトを拡張することもできます。 プロジェクトのサブタイプでは、新しいプロジェクトの種類を記述することがなくプロジェクトを拡張できます。 プロジェクトのサブタイプの詳細については、次を参照してください。 [プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)します。  
  
## <a name="see-also"></a>参照  
 [プロジェクトおよび項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)   
 [項目を追加、新しい項目の追加] ダイアログ ボックス](../Topic/Adding%20Items%20to%20the%20Add%20New%20Item%20Dialog%20Boxes.md)   
 [[新しいプロジェクト] ダイアログ ボックスにディレクトリを追加します。](../Topic/Adding%20Directories%20to%20the%20New%20Project%20Dialog%20Box.md)