---
title: "[新しいプロジェクト] ダイアログ ボックスにディレクトリを追加します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "新しいプロジェクト] ダイアログ ボックスを拡張します。"
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# [新しいプロジェクト] ダイアログ ボックスにディレクトリを追加します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

新しいプロジェクトを作成するときにテンプレートとして使用するためにそれらを表示するに ENT0ENT \[出力\] ダイアログ ボックスに新しいディレクトリを登録できます。  次のコード例では新しいディレクトリ \(ノードを登録する方法について説明します。  例ではVSPackage CLSID\_Package が公開するテンプレートは登録されます。  その結果ENT2ENT \[出力\] ダイアログ ボックスの左側には Folder\_Label\_ResID 特定のリソースで名前が追加されたノードを提供します。  このリソースはVSPackage のサテライト DLL から読み込まれます。  
  
 **フォルダー**  の値は Folder\_Label\_ResID ノードが表示されているフォルダーの GUID を表します。  例ではGUID は ENT2ENT \[出力\] ダイアログ ボックスの \[ENT1ENT\] ペインの \[ENT0ENT\] フォルダーを表します。  **\*\*\* Other Projects \*\*\*** の値がない場合ラベルは最上位に配置されます。  
  
 TemplatesDir の値はプロジェクト テンプレートが格納されているディレクトリの完全パスを指定します。  これらのファイルは.vsz ファイルまたは複製する一般的なテンプレート ファイルを指定できます。  
  
 TemplatesLocalizedSubDir を指定するとローカライズされたテンプレートを保持 TemplatesDir のサブディレクトリを付ける文字列リソースの ID である必要があります。  1 の場合 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] はサテライト DLL の文字列リソースを読み込むための場合サテライト DLL は別のサブディレクトリの名前を含めることができます。 SortPriority の値は並べ替え優先順位を指定します。  
  
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
  
## 参照  
 [プロジェクトおよび項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)   
 [項目を追加、新しい項目の追加\] ダイアログ ボックス](../Topic/Adding%20Items%20to%20the%20Add%20New%20Item%20Dialog%20Boxes.md)   
 [ディレクトリを追加する、新しい項目\] ダイアログ ボックスを追加](../Topic/Adding%20Directories%20to%20the%20Add%20New%20Item%20Dialog%20Box.md)