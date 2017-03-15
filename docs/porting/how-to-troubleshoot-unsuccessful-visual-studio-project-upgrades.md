---
title: "方法: Visual Studio プロジェクトのアップグレードが成功しなかった場合のトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisualStudio.SourceControl.CannotOpenFromSourceControlDSW"
  - "vs.UpgradeProjectSolution.8.0"
helpviewer_keywords: 
  - "アプリケーションのアップグレード、Visual Studio"
  - "アップグレード (プロジェクトを) [Visual Studio]"
  - "プロジェクト [Visual Studio]、アップグレード"
  - "Visual Studio 変換ウィザード"
  - "変換ウィザード"
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 30
caps.handback.revision: 30
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# 方法: Visual Studio プロジェクトのアップグレードが成功しなかった場合のトラブルシューティング
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio が、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の旧バージョンで作成したプロジェクトを完全には変換できない場合があります。  特定の問題が以下のセクションのヒントで解決できない場合、詳細については TechNet の [Wiki: Development Portal \(Wiki: 開発ポータル\)](http://go.microsoft.com/fwlink/?LinkId=254808) を参照してください。  
  
## ファイルが見つからないためプロジェクトを実行できない  
 プロジェクト ファイルには、ユーザーによって F5 キーが押されたときに [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がプロジェクトの実行に使用するハード コーディングされたファイル パスが含まれています。  これらのパスには、devenv.exe やその他の必須ファイルの場所などがあります。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のアップグレード バージョンでは、これらのファイルのパスが変更されている場合があります。  
  
#### ファイル パスの間違いを解決するには  
  
1.  プロジェクト ファイルをテキスト エディターで開きます。  
  
2.  間違っている可能性のあるファイル パス、特に [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョン番号を含むパスをスキャンします。  
  
3.  間違っているファイル パスを、新しいターゲットを指すように変更します。  
  
## 参照が有効でないため、プロジェクトがビルドできない  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のアップグレード時に、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンもアップグレードすることがあります。  新しい [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] バージョンで継承されない参照がプロジェクトに含まれている場合、これらの参照は正しく解決されない可能性があります。  これは特に、`Microsoft.VisualStudio.Shell.Interop.8.0` などのバージョン番号を含む参照で発生する可能性があります。  
  
 コードに無効な参照が多数ある場合、最も簡単な解決策は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の複数バージョン対応機能を使用して [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の旧バージョンをターゲットにすることです。  
  
#### 不適切な参照を解決するには  
  
1.  プロジェクト ファイルをテキスト エディターで開きます。  
  
2.  プロジェクトのプロパティを開きます。  
  
3.  **\[対象のフレームワーク\]** で適切な値を選択します。  または、プロジェクト ファイルの `<TargetFrameworkVersion>` 要素の値を直接変更することもできます。  
  
 アップグレードされた [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] バージョンでプロジェクトを実行する場合は、そのプロジェクトの参照を更新し、参照を呼び出す `Imports` ステートメントまたは `Using` ステートメントも更新する必要があります。  プロジェクトが IDE で読み込まれる場合は、**ソリューション エクスプローラー**または **\[参照マネージャー\]** ダイアログ ボックスを使用して参照を更新できます。  
  
## 参照  
 [\/Upgrade](../ide/reference/upgrade-devenv-exe.md)   
 [Converting to ASP.NET 4](../Topic/Converting%20to%20ASP.NET%204.md)