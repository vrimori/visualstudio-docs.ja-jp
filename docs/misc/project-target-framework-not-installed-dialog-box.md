---
title: "[プロジェクトのターゲット フレームワークがインストールされていません] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.TargetFrameworkNotFound"
ms.assetid: 64ce8743-d5bd-447e-ba10-54b2aafe109e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# [プロジェクトのターゲット フレームワークがインストールされていません] ダイアログ ボックス
お使いのコンピューターにインストールされていないフレームワークを対象とするプロジェクトが開かれました。 続行するには、このダイアログ ボックスのいずれかのオプションを選択する必要があります。  
  
> [!NOTE]
>  新しいフレームワークをダウンロードしてインストールしたときは常に、Visual Studio を再起動する必要があります。  
  
## Visual Basic および Visual C\#  
 Visual Basic プロジェクトまたは Visual C\# プロジェクトを開いた場合は、次のいずれかのオプションを選択します。  
  
 **ターゲットを .NET Framework 4.5 に変更する。後で .NET Framework** *\<バージョン\>* **に戻すことができます。**  
 プロジェクトの対象を .NET Framework 4.5 に再設定します。 以前のバージョンを後で再インストールしてから、プロジェクトの対象を再設定することもできます。  
  
 **.NET Framework \<バージョン\> のターゲット パックをダウンロードします。プロジェクトは変更されません。**  
 必要な .NET Framework のバージョンをダウンロードできる Microsoft ダウンロード センター Web サイトを開きます。 プロジェクトはソリューションからアンロードされます。 目的のフレームワークをダウンロードしてインストールした後に、Visual Studio を再起動し、プロジェクトを開き直す必要があります。  
  
 **プロジェクトをロードしない。**  
 プロジェクトはソリューションからアンロードされたままになります。 後で目的の Framework をインストールし、プロジェクトを再度読み込むことができます。  
  
## Visual C\+\+  
 Visual C\+\+ プロジェクトを開いた場合は、次のいずれかのオプションを選択します。  
  
 **.NET Framework**  *\<バージョン\>*  **のターゲット パックをダウンロードします。プロジェクトは変更されません。**  
 必要な .NET Framework のバージョンをダウンロードできる Microsoft ダウンロード センター Web サイトを開きます。 ダウンロードが完了するとプロジェクトの対象がそのバージョンに再設定されます。 プロジェクトはソリューションからアンロードされます。 目的のフレームワークをダウンロードしてインストールした後に、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を再起動し、プロジェクトを開き直す必要があります。  
  
 **プロジェクトをロードしない。**  
 プロジェクトはソリューションからアンロードされたままになります。 後で目的の Framework をインストールし、プロジェクトを再度読み込むことができます。  
  
## 参照  
 [方法: .NET Framework のバージョンをターゲットにする](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET Framework を対象とするエラーのトラブルシューティング](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [参照の追加](/visual-cpp/ide/adding-references-in-visual-cpp-projects)