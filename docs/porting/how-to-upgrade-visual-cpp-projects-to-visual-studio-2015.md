---
title: "方法: Visual C++ プロジェクトを Visual Studio 2015 にアップグレードする | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト [C++]、アップグレード"
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法: Visual C++ プロジェクトを Visual Studio 2015 にアップグレードする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

旧バージョンの Visual Studio で作成された Visual C\+\+ プロジェクトを初めて開くと、そのプロジェクトを更新するよう求めるメッセージが表示されることがあります。 Visual C\+\+ コンパイラおよびライブラリを最新バージョンにアップグレードするかどうかを確認するメッセージです。 アップグレードのオプションは、プロジェクトの作成に使用された [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョンによって異なります。  
  
 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] を使用して、[!INCLUDE[win8](../debugger/includes/win8_md.md)] で作成された [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] プロジェクトを開き、編集し、ビルドすることができますが、新しい [!INCLUDE[win8](../debugger/includes/win8_md.md)] プロジェクトを作成するには [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] を使用する必要があります \([!INCLUDE[win81](../debugger/includes/win81_md.md)] プロジェクトを作成するには、[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] を使用する必要があります。\)。  
  
 Windows 10 プロジェクトを作成するには、[!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] を使用する必要があります。  
  
 プロジェクトを更新するように求めるメッセージが表示されない場合は、プロジェクトのアップグレードのために何もする必要がない可能性があります。 詳細については、「[Visual Studio プロジェクトの移植、移行、およびアップグレード](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)」を参照してください。  
  
-   プロジェクト \(.vcproj\) が [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] よりも前のバージョンの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で作成されていた場合は、プロジェクトを更新する必要があります。  
  
-   プロジェクト \(.vcxproj\) が [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]、[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]、または [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] で作成されている場合、次の 2 つのオプションがあります。  
  
    -   更新をスキップできます。[!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] が [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1、[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]、または [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] の Visual C\+\+ ツールにアクセスできる場合、プロジェクトは変更を加えずに読み込まれます。 そのアクセスを可能にするには、プロジェクトの作成に使用したバージョンの Visual Studio を、[!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] と同じマシンにインストールします。 詳細については、「[複数バージョンの Visual Studio のインストール](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md)」を参照してください。  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] が後で説明するような変更を加えられるようにすることで、プロジェクトを更新できます。 ソリューションに複数の Visual C\+\+ プロジェクトが含まれる場合は、すべてのプロジェクトを更新する必要があります。  
  
        > [!NOTE]
        >  最初に更新を求められたときに更新しない場合は、後で **\[プロジェクト\]** メニューの **\[VC\+\+ プロジェクトの更新\]** を選択してプロジェクトを更新できます。 このコマンドが表示されない場合、更新は必要ではありません。  
  
## Visual C\+\+ プロジェクトのアップグレード  
 [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] が自動的にプロジェクトを更新できるようにすると、次の変更が加えられます。  
  
-   [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] のコンパイラおよびライブラリを使用するように、プロジェクトを変更します \(PlatformToolset \= VisualStudio v140\)。  
  
-   [!INCLUDE[cppcli](../misc/includes/cppcli_md.md)] プロジェクトの場合は、TargetFrameworkVersion を .NET Framework 4.5.2 に変更します。  
  
## カスタム PlatformToolset の使用の継続  
 [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] でカスタム PlatformToolset を引き続き使用する場合、ツールセットは、x86 コンピューターでは %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ の下、x64 コンピューターでは %ProgramFiles \(x86\)%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ の下に格納されている必要があります。 カスタム PlatformToolset を作成する方法については、Visual C\+\+ チーム ブログの「[C\+\+ ネイティブ マルチ ターゲット](http://go.microsoft.com/fwlink/?LinkId=248587)」を参照してください。  
  
## 参照  
 [Visual Studio プロジェクトの移植、移行、およびアップグレード](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)